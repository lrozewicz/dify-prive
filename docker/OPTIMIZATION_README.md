# Dify Optimized Configuration for 8GB RAM / 4 CPU Server

## 📊 Resource Allocation Overview

### Total Resources Available
- **RAM**: 8GB
- **CPU**: 4 cores

### Resource Limits per Service

| Service | RAM Limit | RAM Reserved | CPU Limit | CPU Reserved | Priority |
|---------|-----------|--------------|-----------|--------------|----------|
| **db** (PostgreSQL) | 1.5 GB | 768 MB | 1.5 | 0.5 | High |
| **weaviate** (Vector DB) | 1.5 GB | 768 MB | 1.5 | 0.5 | High |
| **api** | 1.5 GB | 768 MB | 1.5 | 0.5 | High |
| **worker** | 1.5 GB | 768 MB | 1.5 | 0.5 | High |
| **plugin_daemon** | 768 MB | 384 MB | 1.0 | 0.25 | Medium |
| **web** | 768 MB | 384 MB | 1.0 | 0.25 | Medium |
| **redis** | 512 MB | 256 MB | 0.5 | 0.25 | Medium |
| **sandbox** | 512 MB | 256 MB | 0.5 | 0.25 | Medium |
| **worker_beat** | 256 MB | 128 MB | 0.5 | 0.25 | Low |
| **nginx** | 256 MB | 128 MB | 0.5 | 0.25 | Low |
| **ssrf_proxy** | 256 MB | 128 MB | 0.5 | 0.25 | Low |
| **TOTAL** | ~9.3 GB | ~4.6 GB | ~10 | ~3.5 | - |

### Notes on Resource Allocation

- **Limits** can exceed total RAM (9.3 GB > 8 GB) because not all services will hit their limit simultaneously
- **Reservations** (4.6 GB) are guaranteed and safely under the 8 GB total
- **CPU limits** can burst above 4 cores when needed, but reservations ensure minimum performance
- Services are prioritized: database, vector store, and API get most resources

## 🚀 How to Use

### Option 1: Use Web Editor in Portainer (Recommended)

1. **In Portainer**:
   - Go to **Stacks** → **Add Stack**
   - Choose **Web editor**
   - Name: `dify`

2. **Paste docker-compose content**:
   - Copy entire contents of `docker-compose.optimized.yaml`
   - Paste into the editor

3. **Add environment variables**:
   - Scroll to **Environment variables** section
   - Click **Advanced mode**
   - Copy and paste entire contents of `.env.prod`

4. **Deploy**:
   - Click **Deploy the stack**

### Option 2: Use Git Repository

1. **Create a fork** of Dify repository
2. **Copy optimized files** to your fork
3. **In Portainer**:
   - Go to **Stacks** → **Add Stack**
   - Choose **Repository**
   - Set Repository URL to your fork
   - Set Compose path: `docker/docker-compose.optimized.yaml`
   - Upload `.env.prod` file or paste env variables

### Option 2: Keep Both Files (Flexible)

Keep both `docker-compose.yaml` (original) and `docker-compose.optimized.yaml` side by side.

In Portainer, specify the optimized file:
- Compose path: `docker/docker-compose.optimized.yaml`

## ⚙️ Optimized .env.prod Settings

Key optimizations in `.env.prod`:

```bash
# Worker Configuration (optimized for 4 CPU cores)
SERVER_WORKER_AMOUNT=2          # 2 API workers (4 cores / 2 + 1 ≈ 2-3)
CELERY_WORKER_AMOUNT=2          # 2 Celery workers for background tasks
PM2_INSTANCES=2                 # 2 PM2 instances for Next.js

# PostgreSQL Configuration (optimized for 8GB RAM)
POSTGRES_SHARED_BUFFERS=512MB   # Increased from 128MB
POSTGRES_EFFECTIVE_CACHE_SIZE=2GB  # Decreased from 4GB (25% of 8GB)
POSTGRES_MAX_CONNECTIONS=100    # Sufficient for typical workload

# Redis Configuration
# Redis has maxmemory=512mb set in docker-compose with LRU eviction policy

# Nginx Configuration
NGINX_WORKER_PROCESSES=2        # Matches CPU cores for optimal performance
```

## 📈 Performance Expectations

### What to Expect
✅ Smooth operation for typical Dify workloads:
- 5-10 concurrent users
- Standard document processing (PDFs, text files)
- Regular LLM queries and conversations
- Knowledge base operations

### When You Might Need More Resources
⚠️ Consider upgrading if you experience:
- 20+ concurrent users regularly
- Very large documents (100+ MB)
- Heavy batch processing operations
- Multiple large knowledge bases (1000+ documents each)

## 🔍 Monitoring Resources

### Check Resource Usage in Portainer

1. Go to **Stacks** → Click on `dify` stack
2. Click on **Containers**
3. Click on individual container → **Stats** tab
4. Monitor CPU % and Memory usage

### Via Docker CLI

```bash
# Check all container stats
docker stats

# Check specific container
docker stats dify-api-1

# Check resource limits
docker inspect dify-api-1 | grep -A 10 "Memory"
```

### Warning Signs to Watch

🔴 **High Memory Usage** (>90% consistently):
- Consider reducing `SERVER_WORKER_AMOUNT` to 1
- Reduce `CELERY_WORKER_AMOUNT` to 1
- Decrease `POSTGRES_SHARED_BUFFERS` to 256MB

🔴 **High CPU Usage** (>80% consistently):
- Reduce `PM2_INSTANCES` to 1
- Consider fewer concurrent workers

🟡 **Swap Usage** (if enabled):
- This indicates RAM is insufficient
- Optimize further or upgrade server RAM

## 🛠️ Troubleshooting

### OOM (Out of Memory) Errors

If you see containers being killed due to OOM:

1. **Reduce worker counts**:
   ```bash
   SERVER_WORKER_AMOUNT=1
   CELERY_WORKER_AMOUNT=1
   PM2_INSTANCES=1
   ```

2. **Lower PostgreSQL buffers**:
   ```bash
   POSTGRES_SHARED_BUFFERS=256MB
   POSTGRES_EFFECTIVE_CACHE_SIZE=1GB
   ```

3. **Restart stack**:
   ```bash
   docker-compose down
   docker-compose up -d
   ```

### Slow Performance

1. **Check if services are hitting memory limits**:
   ```bash
   docker stats --no-stream --format "table {{.Container}}\t{{.MemUsage}}\t{{.MemPerc}}"
   ```

2. **Increase limits for bottleneck services** (if RAM allows):
   - Edit `docker-compose.optimized.yaml`
   - Increase `deploy.resources.limits.memory` for slow service
   - Redeploy stack

3. **Enable Redis persistence** (if needed):
   - Add `--save 60 1000` to Redis command
   - This trades some performance for data durability

## 📝 Configuration Files

### Files Included

1. **docker-compose.optimized.yaml**
   - Optimized version with resource limits
   - Ready for 8GB RAM / 4 CPU servers

2. **.env.prod**
   - Updated with optimal worker counts
   - PostgreSQL tuned for 8GB RAM
   - All security keys changed

3. **OPTIMIZATION_README.md** (this file)
   - Documentation and usage guide

## 🔄 Upgrading Dify

When upgrading to a new Dify version:

1. **Check for changes** in official docker-compose.yaml:
   ```bash
   git diff main..upstream/main docker/docker-compose.yaml
   ```

2. **Merge changes** into `docker-compose.optimized.yaml`

3. **Preserve resource limits** during merge

4. **Test** before deploying to production

## 📊 Comparison: Original vs Optimized

| Aspect | Original | Optimized |
|--------|----------|-----------|
| Resource limits | None | Yes, per service |
| OOM protection | ❌ No | ✅ Yes |
| Guaranteed resources | ❌ No | ✅ Yes (reservations) |
| Worker optimization | Default (1) | Tuned for 4 CPU (2) |
| PostgreSQL tuning | Generic | 8GB server specific |
| Redis memory limit | Unlimited | 512MB with LRU |
| Risk of system crash | High | Low |

## 🎯 Best Practices

1. **Monitor regularly**: Check Portainer Stats weekly
2. **Backup before changes**: Always backup volumes before updates
3. **Test limits**: Try stress testing in non-production first
4. **Gradual scaling**: If adding users, monitor and adjust limits
5. **Plan for growth**: Consider 16GB RAM upgrade when hitting 70% usage regularly

## 📧 Support

If you encounter issues:

1. Check logs: `docker logs <container-name>`
2. Review Portainer Stack logs
3. Verify `.env.prod` settings match this guide
4. Ensure DNS and Nginx Proxy Manager are configured correctly

## 🔐 Security Notes

- All default passwords in `.env.prod` have been changed to secure values
- Keep `.env.prod` file secure - never commit to public repos
- Regularly update Docker images for security patches
- Monitor for unusual resource usage patterns

---

**Last Updated**: 2025-11-01
**Optimized For**: 8GB RAM, 4 CPU cores
**Tested With**: Dify v1.9.2

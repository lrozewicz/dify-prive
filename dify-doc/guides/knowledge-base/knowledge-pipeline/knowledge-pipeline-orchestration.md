# Step 2: Knowledge Pipeline Orchestration

Imagine setting up a factory production line where each station (node) performs a specific task, and you connect them to assemble widgets into a final product. This is knowledge pipeline orchestration—a visual workflow builder that allows you to configure data processing sequences through a drag-and-drop interface. It provides control over document ingestion, processing, chunking, indexing, and retrieval strategies.

In this section, you'll learn about the knowledge pipeline process, understand different nodes, how to configure them, and customize your own data processing workflows to efficiently manage and optimize your knowledge base.

### Interface Status

When entering the knowledge pipeline orchestration canvas, you’ll see:

* **Tab Status**: Documents, Retrieval Test, and Settings tabs will be grayed out and unavailable at the moment
* **Essential Steps**: You must complete knowledge pipeline orchestration and publishing before uploading files

Your starting point depends on the template choice you made previously. If you chose **Blank Knowledge Pipeline**, you'll see a canvas that contains Knowledge Base node only. There'll be a note with guide next to the node that walks you through the general steps of pipeline creation.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3938d727600c6a85d80fc5b04854dcfc" alt="Blank Pipeline" data-og-width="1280" width="1280" data-og-height="652" height="652" data-path="images/knowledge-base/create-knowledge-pipeline-8.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=dba9966ff2a8c3e51a22fc4a9a38c122 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=04150ae5d3dcebde8f23abfc155d0a85 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=12de9c05a53df86089191d1f44141cf9 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=06e01e2f56f0dd78fe351e380dc55f2d 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=b36dc3f80e960067368623e9c10f7c3f 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-8.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=984fcc7a72957e73c8f32f7406cceb73 2500w" />

If you selected a specific pipeline template, there'll be a ready-to-use workflow that you can use or modify on the canvas right away.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f422cb3a9bdb2b8e0a8608c5987e9052" alt="Template Pipeline" data-og-width="1280" width="1280" data-og-height="637" height="637" data-path="images/knowledge-base/create-knowledge-pipeline-9.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3bfdb01b50d5bd9f85b53dcf370142ce 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c7cd1c32cf0f8fa46ee4e32f6fad9081 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3852fb75f2d0d24cc3431c5d71ffa592 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=b8cd32c2eb5d7a8d71606676adf83f20 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5fe2dfe349ded06364c351a78648b083 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/create-knowledge-pipeline-9.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ccb8d0106eca8369299744b237ad6693 2500w" />

## The Complete Knowledge Pipeline Process

Before we get started, let's break down the knowledge pipeline process to understand how your documents are transformed into a searchable knowledge base.

The knowledge pipeline includes these key steps:

<Tip>
  Data Source → Data Processing (Extractor + Chunker) → Knowledge Base Node (Chunk Structure + Retrieval Setting) → User Input Field → Test & Publish
</Tip>

1. **Data Source**: Content from various data sources (local files, Notion, web pages, etc.)
2. **Data Processing**: Process and transform data content
   * Extractor: Parse and structure document content
   * Chunker: Split structured content into manageable segments
3. **Knowledge Base**: Set up chunk structure and retrieval settings
4. **User Input Field**: Define parameters that pipeline users need to input for data processing
5. **Test & Publish**: Validate and officially activate the knowledge base

***

## Step 1: Data Source

In a knowledge base, you can choose single or multiple data sources. Currently, Dify supports 4 types of data sources: **file upload, online drive, online documents, and web crawler**.

Visit the [Dify Marketplace](https://marketplace.dify.ai) for more data sources.

### File Upload

Upload local files through drag-and-drop or file selection.

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3cf88cfdf65edb4cc9b496c187780e33" alt="" data-og-width="934" width="934" data-og-height="1140" height="1140" data-path="images/knowledge-base/knowledge-pipeline-orchestration-1.PNG" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=6da1f757a8a515368ac0650c8962e8fe 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5a4d64bb33473d104cf50884f9af87d5 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=29fb2e601c5fc26e9c60717afa6c2d35 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=05b4b89f502caec91bdf63b078cc4f32 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=2ea2e85b591ad153d42809afea36c39c 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-1.PNG?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=fae7db585a3cc27a7b884cfbac143492 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    **Configuration Options**

    | Item          | Description                                                                                       |
    | ------------- | ------------------------------------------------------------------------------------------------- |
    | File Format   | Support PDF, XLSX, DOCX, etc. Users can customize their selection                                 |
    | Upload Method | Upload local files or folders through drag-and-drop or file selection. Batch upload is supported. |

    **Limitations**

    | Item          | Description                                                                                       |
    | ------------- | ------------------------------------------------------------------------------------------------- |
    | File Quantity | Maximum 50 files per upload                                                                       |
    | File Size     | Each file must not exceed 15MB                                                                    |
    | Storage       | Limits on total document uploads and storage space may vary for different SaaS subscription plans |

    **Output Variables**

    | Output Variable | Format          |
    | --------------- | --------------- |
    | `{x} Document`  | Single document |
  </div>
</div>

***

### Online Document

#### Notion

Integrate with your Notion workspace to seamlessly import pages and databases, always keeping your knowledge base automatically updated.

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3fe8dd70bef6d58a8751785eae260c1e" alt="Notion" data-og-width="908" width="908" data-og-height="1140" height="1140" data-path="images/knowledge-base/knowledge-pipeline-orchestration-2.PNG" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=61c67e03b01098af5d49b11dffaa1c11 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=69165104ecd84f4c1c7ab6139bd09175 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=60c142f58eaa015faeaae9906c10b7bb 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=6848a1573416ed4008270c1e133385cc 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=40e4e5a79aca8181f343928dc2d31f31 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-2.PNG?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=622abc80a5a57cb6799da581c1345e87 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    **Configuration Options**

    | Item      | Option   | Output Variable | Description                          |
    | --------- | -------- | --------------- | ------------------------------------ |
    | Extractor | Enabled  | `{x} Content`   | Structured and processed information |
    |           | Disabled | `{x} Document`  | Original text                        |
  </div>
</div>

***

### Web Crawler

Transform web content into formats that can be easily read by large language models. The knowledge base supports Jina Reader and Firecrawl.

#### Jina Reader

An open-source web parsing tool providing simple and easy-to-use API services, suitable for fast crawling and processing web content.

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=0306d19e1131aef280622011fe680d41" alt="Jina Reader" data-og-width="566" width="566" data-og-height="848" height="848" data-path="images/knowledge-base/knowledge-pipeline-orchestration-3.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=965a2b443f2c79d933a116723af33273 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=95d9d828233c5e3eb744285256617fa2 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=8e73163106884460c796f516db30cd72 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=24d4c7311035a938def5a228a824cd4a 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3b7ac0b5acda6542131a0bb13b06cec7 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-3.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=acfe304d848a2de2a74d74d78f821018 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    **Parameter Configuration**

    | Parameter        | Type     | Description                          |
    | ---------------- | -------- | ------------------------------------ |
    | URL              | Required | Target webpage address               |
    | Crawl sub-page   | Optional | Whether to crawl linked pages        |
    | Use sitemap      | Optional | Crawl by using website sitemap       |
    | Limit            | Required | Set maximum number of pages to crawl |
    | Enable Extractor | Optional | Choose data extraction method        |
  </div>
</div>

#### Firecrawl

An open-source web parsing tool that provides more refined crawling control options and API services. It supports deep crawling of complex website structures, recommended for batch processing and precise control.

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=398423f8e068968f2fc848673d14fdcb" alt="" data-og-width="714" width="714" data-og-height="1412" height="1412" data-path="images/knowledge-base/knowledge-pipeline-orchestration-4.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=70e0a521b5cff0f67cab50a65750efb9 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c9b486bed96c087979c318d8c00d484a 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=27166ebd8c575ede3f9021641da7a120 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=a69029473a4894dc195213118a90456d 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f8e2c1e4560c5e458d7b1fbbaef4a0a5 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f34c1c627409cd5712eb0cc19c831f22 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    **Parameter Configuration**

    | Parameter                 | Type     | Description                                                                |
    | ------------------------- | -------- | -------------------------------------------------------------------------- |
    | URL                       | Required | Target webpage address                                                     |
    | Limit                     | Required | Set maximum number of pages to crawl                                       |
    | Crawl sub-page            | Optional | Whether to crawl linked pages                                              |
    | Max depth                 | Optional | How many levels deep the crawler will traverse from the starting URL       |
    | Exclude paths             | Optional | Specify URL patterns that should not be crawled                            |
    | Include only paths        | Optional | Crawl specified paths only                                                 |
    | Extractor                 | Optional | Choose data processing method                                              |
    | Extract Only Main Content | Optional | Isolate and retrieve the primary, meaningful text and media from a webpage |
  </div>
</div>

***

### Online Drive

Connect your online cloud storage services (e.g., Google Drive, Dropbox, OneDrive) and let Dify automatically retrieve your files. Simply select and import the documents you need for processing, without manually downloading and re-uploading files.

<Tip>
  Need help with authorization? Please check [Authorize Data Source](/en/guides/knowledge-base/knowledge-pipeline/authorize-data-source) for detailed guidance on authorizing different data sources.
</Tip>

***

## Step 2: Set Up Data Processing Tools

In this stage, these tools extract, chunk, and transform the content for optimal knowledge base storage and retrieval. Think of this step like meal preparation. We clean raw materials up, chop them into bite-sized pieces, and organize everything, so the dish can be cooked up quickly when someone orders it.

### Doc Processor

Documents come in different formats - PDF, XLSX, DOCX. However, LLM can't read these files directly. That's where extractors come in. They support multiple formats and handle the conversion, so your content is ready for the next step of the LLMs.

You can choose Dify's Doc Extractor to process files, or select tools based on your needs from Marketplace which offers Dify Extractor and third-party tools such as Unstructured.

#### Doc Extractor

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=730bf3fa7d78750a4e663fea9e4f7386" alt="" data-og-width="500" width="500" data-og-height="200" height="200" data-path="images/knowledge-base/knowledge-pipeline-orchestration-4-1.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=9475c8d3ff87d6dc0e97d39192ffe467 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=daa850d64348af3be23bf8e36a35bbfb 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=93f2351dda9074df9acec48f66ea190d 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=a0a66b97fa02fbc14a8c4d4bddfb8d2b 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5a801881394688e1fdab0b9abf7d614d 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-4-1.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3caa849645b5a7fb2a1247d2cda7b048 2500w" />

As an information processing center, document extractor node identifies and reads files from input variables, extracts information, and finally converts them into a format that works with the next node.

<Tip>
  For more information, please refer to the [Document Extractor](/en/guides/workflow/node/doc-extractor).
</Tip>

#### Dify Extractor

Dify Extractor is a built-in document parser presented by Dify. It supports multiple common file formats and is specially optimized for Doc files. It can extract and store images from documents and return image URLs.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=01c59fc4966df40b70e611b2a1ac2a74" alt="Dify Extractor" data-og-width="500" width="500" data-og-height="200" height="200" data-path="images/knowledge-base/knowledge-pipeline-orchestration-5.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=7a9004471c0ddeee518a3eb7d33e0e22 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=17b4db717bb0f09efc76850180d71f39 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=133d95d671d3c1372e230629542946b0 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=acedb2ba68e78e780e75d367c0f63c3a 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=64dbdec1d9cdb07131062f91a3a114e3 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-5.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=b63bfd5fd1cf6e404f1f239b701a4f42 2500w" />

#### Unstructured

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=505b3dad32bfe8f9f3949438e592897f" alt="Unstructured" data-og-width="470" width="470" data-og-height="550" height="550" data-path="images/knowledge-base/knowledge-pipeline-orchestration-7.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=42c739205bed3f9120277a74a7644bbe 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ca88cd5d4e141fdb3085c9b7f1b2f531 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=673f0a62a0a4a07887bc86889e2ba1e2 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=52c288e70129dbe5a04724cd87e4f4bb 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=d45de7d4cc9b7e7f3f1e2da3774b7c1d 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-7.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=61d80e86f8f1a099b59f73846539fb68 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    [Unstructured](https://marketplace-staging.dify.dev/plugins/langgenius/unstructured) transforms documents into structured, machine-readable formats with highly customizable processing strategies. It offers multiple extraction strategies (auto, hi\_res, fast, OCR-only) and chunking methods (by\_title, by\_page, by\_similarity) to handle diverse document types, offering detailed element-level metadata including coordinates, confidence scores, and layout information. It’s recommended for enterprise document workflows, processing of mixed file types, and cases that require precise control over document processing parameters.
  </div>
</div>

<Tip>
  Explore more tools in the [Dify Marketplace](https://marketplace.dify.ai).
</Tip>

***

### Chunker

Similar to human limited attention span, large language models cannot process huge amount of information simultaneously. Therefore, after information extraction, the chunker splits large document content into smaller and manageable segments (called "chunks").

Different documents require different chunking strategies. A product manual works best when split by product features, while research papers should be divided by logical sections. Dify offers 3 types of chunkers for various document types and use cases.

#### Overview of Different Chunkers

| Chunker Type         | Highlights                                            | Best for                                              |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| General Chunker      | Fixed-size chunks with customizable delimiters        | Simple documents with basic structure                 |
| Parent-child Chunker | Dual-layer structure: precise matching + rich context | Complex documents requiring rich context preservation |
| Q\&A Processor       | Processes question-answer pairs from spreadsheets     | Structured Q\&A data from CSV/Excel files             |

#### Common Text Pre-processing Rules

All chunkers support these text cleaning options:

| Preprocessing Option                          | Description                                                                        |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| Replace consecutive spaces, newlines and tabs | Clean up formatting by replacing multiple whitespace characters with single spaces |
| Remove all URLs and email addresses           | Automatically detect and remove web links and email addresses from text            |

#### General Chunker

Basic document chunking processing, suitable for documents with relatively simple structures. You can configure text chunking and text preprocessing rules according to the following configuration.

**Input and Output Variable**

| Type            | Variable           | Description                                                                 |
| --------------- | ------------------ | --------------------------------------------------------------------------- |
| Input Variable  | `{x} Content`      | Complete document content that the chunker will split into smaller segments |
| Output Variable | `{x} Array[Chunk]` | Array of chunked content, each segment optimized for retrieval and analysis |

**Chunk Settings**

| Configuration Item   | Description                                                                                                                                                                                              |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Delimiter            | Default value is `\n` (line breaks for paragraph segmentation). You can customize chunking rules following regex. The system will automatically execute segmentation when the delimiter appears in text. |
| Maximum Chunk Length | Specifies the maximum character limit within a segment. When this length is exceeded, forced segmentation will occur.                                                                                    |
| Chunk Overlap        | When segmenting data, there is some overlap between segments. This overlap helps improve information retention and analysis accuracy, enhancing recall effectiveness.                                    |

#### Parent-child Chunker

By using a dual-layer segmentation structure to resolve the contradiction between context and accuracy, parent-child clunker achieves the balance between precise matching and comprehensive contextual information in Retrieval Augmented Generation (RAG) systems.

**How Parent-child Chunker Works**

Child Chunks for query matching: Small, precise information segments (usually single sentences) to match user queries with high accuracy.

Parent Chunks provide rich context: Larger content blocks (paragraphs, sections, or entire documents) that contain the matching child chunks, giving the large language model (LLM) comprehensive background information.

| Type            | Variable                 | Description                                                                 |
| --------------- | ------------------------ | --------------------------------------------------------------------------- |
| Input Variable  | `{x} Content`            | Complete document content that the chunker will split into smaller segments |
| Output Variable | `{x} Array[ParentChunk]` | Array of parent chunks                                                      |

**Chunk Settings**

| Configuration Item          | Description                                                                                                                         |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Parent Delimiter            | Set delimiter for parent chunk splitting                                                                                            |
| Parent Maximum Chunk Length | Set maximum character count for parent chunks                                                                                       |
| Child Delimiter             | Set delimiter for child chunk splitting                                                                                             |
| Child Maximum Chunk Length  | Set maximum character count for child chunks                                                                                        |
| Parent Mode                 | Choose between Paragraph (split text into paragraphs) or "Full Document" (use entire document as parent chunk) for direct retrieval |

#### Q\&A Processor

Combining extraction and chunking in one node, Q\&A Processor is specifically designed for structured Q\&A datasets from CSV and Excel files. Perfect for FAQ lists, shift schedules, and any spreadsheet data with clear question-answer pairs.

**Input and Output Variable**

| Type            | Variable             | Description   |
| --------------- | -------------------- | ------------- |
| Input Variable  | `{x} Document`       | A single file |
| Output Variable | `{x} Array[QAChunk]` | QA chunk      |

**Variable Configuration**

| Configuration Item         | Description                    |
| -------------------------- | ------------------------------ |
| Column Number for Question | Set content column as question |
| Column Number for Answer   | Set column answer as answer    |

***

## Step 3: Configure Knowledge Base Node

Now that your documents are processed and chunked, it's time to set up how they'll be stored and retrieved. Here, you can select different indexing methods and retrieval strategies based on your specific needs.

Knowledge base node configuration includes: Input Variable, Chunk Structure, Index Method, and Retrieval Settings.

### Chunk Structure

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=05d101a6af483cfb1ebe5e23b7ec9647" alt="Chunk Structure" data-og-width="1086" width="1086" data-og-height="1036" height="1036" data-path="images/knowledge-base/knowledge-pipeline-orchestration-8.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=cd6a0356fdf6eecc235aaf3e74a71927 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f985b6669df8841e99d617fb039ed6c9 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=44172e45ab85d78b024d65835cb0388f 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=660217abab3091831ff16d5900278f52 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=9545663b790e59e4458a7ca761a4f444 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-8.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3429a706398f7a1bc9e8c8aaef07eb8d 2500w" />

Chunk structure determines how the knowledge base organizes and indexes your document content. Choose the structure mode that best fits your document type, use case, and cost.

The knowledge base supports three chunk modes: **General Mode, Parent-child Mode, and Q\&A Mode**. If you're creating a knowledge base for the first time, we recommend choosing Parent-child Mode.

<Warning>
  **Important Reminder**: Chunk structure cannot be modified once saved and published. Please choose carefully.
</Warning>

#### General Mode

Suitable for most standard document processing scenarios. It provides flexible indexing options—you can choose appropriate indexing methods based on different quality and cost requirements.

General mode supports both high-quality and economical indexing methods, as well as various retrieval settings.

#### Parent-child Mode

It provides precise matching and corresponding contextual information during retrieval, suitable for professional documents that need to maintain complete context.

Parent-child mode supports HQ (High Quality) mode only, offering child chunks for query matching and parent chunks for contextual information during retrieval.

#### Q\&A Mode

Create documents that pair questions with answers when using structured question-answer data. These documents are indexed based on the question portion, enabling the system to retrieve relevant answers based on query similarity.

Q\&A Mode supports HQ (High Quality) mode only.

### Input Variable

Input variables receive processing results from data processing nodes as the data source for knowledge base. You need to connect the output from chunker to the knowledge base as input.

The node supports different types of standard inputs based on the selected chunk structure:

* **General Mode**: x Array\[Chunk] - General chunk array
* **Parent-child Mode**: x Array\[ParentChunk] - Parent chunk array
* **Q\&A Mode**: x Array\[QAChunk] - Q\&A chunk array

### Index Method & Retrieval Setting

The index method determines how your knowledge base builds content indexes, while retrieval settings provide corresponding retrieval strategies based on the selected index method. Think of it in this way: index method determines how to organize your documents, while retrieval settings tell users what methods they can use to find documents.

The knowledge base provides two index methods: **High Quality** and **Economy**, each offering different retrieval setting options.

High quality mode uses embedding models to convert segmented text blocks into numerical vectors, helping to compress and store large amounts of text information more effectively. This enables the system to find semantically relevant accurate answers even when the user's question wording doesn't exactly match the document.

In economy mode, each block uses 10 keywords for retrieval without calling embedding models, generating no costs.

<Tip>
  Please refer to [Select the Indexing Method and Retrieval Setting](/en/guides/knowledge-base/create-knowledge-and-upload-documents/setting-indexing-methods) for more details.
</Tip>

#### Index Methods and Retrieval Settings

| Index Method | Available Retrieval Settings | Description                                                             |
| ------------ | ---------------------------- | ----------------------------------------------------------------------- |
| High Quality | Vector Retrieval             | Understand deeper meaning of queries based on semantic similarity       |
|              | Full-text Retrieval          | Keyword-based retrieval providing comprehensive search capabilities     |
|              | Hybrid Retrieval             | Combine both semantic and keywords                                      |
| Economy      | Inverted Index               | Common search engine retrieval method, matches queries with key content |

You can also refer to the table below for information on configuring chunk structure, indexing methods, parameters, and retrieval settings.

| Chunk Structure   | Index Methods                             | Parameters                                              | Retrieval Settings                                                                        |
| ----------------- | ----------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| General mode      | High Quality <br /> <br /> <br /> Economy | Embedding Model <br /> <br /> <br /> Number of Keywords | Vector Retrieval <br /> Full-text Retrieval <br /> Hybrid Retrieval <br /> Inverted Index |
| Parent-child Mode | High Quality Only                         | Embedding Model                                         | Vector Retrieval <br /> Full-text Retrieval <br /> Hybrid Retrieval                       |
| Q\&A Mode         | High Quality Only                         | Embedding Model                                         | Vector Retrieval <br /> Full-text Retrieval <br /> Hybrid Retrieval                       |

***

## Step 4: Create User Input Form

User input forms are essential for collecting the initial information your pipeline needs to run effectively. Similar to [start node](/en/guides/workflow/node/start) in workflow, this form gathers necessary details from users - such as files to upload, specific parameters for document processing - ensuring your pipeline has all the information it needs to deliver accurate results.

This way, you can create specialized input forms for different use scenarios, improving pipeline flexibility and usability for various data sources or document processing steps.

### Create User Input Form

There're two ways to create user input field:

1. **Pipeline Orchestration Interface**\
   Click on the **Input field** to start creating and configuring input forms.\\
   <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=98ed68b0f89e283381d80e767c1ba570" alt="" data-og-width="962" width="962" data-og-height="130" height="130" data-path="images/knowledge-base/knowledge-pipeline-orchestration-9.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=9188b499bdc75b49a2a455269f0fe6f6 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=44058a23d939795c19936459f6b31a66 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5bdf5b9d224dfb2aa8f813acff106a2b 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=89ff54aa268873f954008dde5966bce6 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=bbf97ea2c1f2454f08fde0b7d6f2bd4a 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-9.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=579926b47b2775e6df1dcf2dbefb25da 2500w" />
2. **Node Parameter Panel**\
   Select a node. Then, in parameter input on the right-side panel, click + Create user input for new input items. New input items will also be collected in the Input Field. <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=641daa36a3cf66f98afcd989fd602512" alt="" data-og-width="740" width="740" data-og-height="528" height="528" data-path="images/knowledge-base/knowledge-pipeline-orchestration-10.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=0a4ed61e5229887b8cd6762eebe3d6c4 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=e775260b0e9cc751134b1aaaf47c6b61 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=731cf1e2d688767f5b2b6d0f41e54c0e 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=08634906a69c35c4e46c525e6e6ade55 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=96953f01f002469e279f573a67834827 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-10.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c57d4e4d3fc635f14aba18b8b13758c6 2500w" />

### Add User Input Fields

#### Unique Inputs for Each Entrance

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=503ff9f3674f1c7f5d706c14d4c8bfdc" alt="" data-og-width="861" width="861" data-og-height="1280" height="1280" data-path="images/knowledge-base/knowledge-pipeline-orchestration-11.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=7d5e580f84cdad95c61822d3f16fadeb 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=10787f38d4245daef3621ffbd7b37784 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=8ae9133e1bfdfb4b5e6d0116570da49f 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c5a87da6852a84652e6093ae13f22e91 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=003e9d2dbdc78e8394fca1be6bd48396 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-11.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=e1b3bc68e943eedfc8c176a0186784a0 2500w" />

These inputs are specific to each data source and its downstream nodes. Users only need to fill out these fields when selecting the corresponding data source, such as different URLs for different data sources.

**How to create**: Click the `+` button on the right side of a data source to add fields for that specific data source. These fields can only be referenced by that data source and its subsequently connected nodes. <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=18b15f2570177844dbae96aa66c7ab95" alt="" data-og-width="800" width="800" data-og-height="206" height="206" data-path="images/knowledge-base/knowledge-pipeline-orchestration-12.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=df74440ce812d1dee424191026307f22 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c5d35aea6136e45b881589c19d181932 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=6d5e2eabf9088452f3ca261331af4d2c 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=d57379c5baecc8a60c812531ad098eb3 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=53a020de7662a049332b710f1d3aeb59 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-12.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=46ffe0a9fd7fae7e9634b337bd151726 2500w" />

#### Global Inputs for All Entrances

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ea8ca2414564dd8e629108bfb053194b" alt="" data-og-width="770" width="770" data-og-height="442" height="442" data-path="images/knowledge-base/knowledge-pipeline-orchestration-13.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=7be4eca8a2734863eda9148efce57767 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5bc92de14490857816e793057b066099 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=249765b1ae0a2a9aea980f8183b48faa 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=c5c003cf226717d4942360c339c2931e 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=bca97f6d81d146d77140d5040afa57e5 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-13.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=472d45ba2de2824eb3bf055f0a713d0d 2500w" />

Global shared inputs can be referenced by all nodes. These inputs are suitable for universal processing parameters, such as delimiters, maximum chunk length, document processing configurations, etc. Users need to fill out these fields regardless of which data source they choose.

**How to create**: Click the `+` button on the right side of Global Inputs to add fields that can be referenced by any node.

### Supported Input Field Types

The knowledge pipeline supports seven types of input variables:

<div style={{ display:"flex",flexWrap:"wrap",gap:"30px" }}>
  <div style={{ flex:1,minWidth:"200px" }}>
        <img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=6035e9852afa8a899753b75b29d1e988" alt="" data-og-width="770" width="770" data-og-height="686" height="686" data-path="images/knowledge-base/knowledge-pipeline-orchestration-14.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=702d076a8ace3de75e4caf22ef7a93d8 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=e4e5e49591e28b922aa55b493c5f89f7 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f0bed67b69f790fc7c1328e0afb8e9be 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f11b266db790d71ff05bec61d23f227e 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=4cdebd3b8ac52b4f0f61b5dbca88b806 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-14.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=bc9b363939d5f4f779f04557a5e641b5 2500w" />
  </div>

  <div style={{ flex:2,minWidth:"300px" }}>
    | Field Type | Description                                                                                         |
    | ---------- | --------------------------------------------------------------------------------------------------- |
    | Text       | Short text input by knowledge base users, maximum length 256 characters                             |
    | Paragraph  | Long text input for longer character strings                                                        |
    | Select     | Fixed options preset by the orchestrator for users to choose from, users cannot add custom content  |
    | Boolean    | Only true/false values                                                                              |
    | Number     | Only accepts numerical input                                                                        |
    | Single     | Upload a single file, supports multiple file types (documents, images, audio, and other file types) |
    | File List  | Batch file upload, supports multiple file types (documents, images, audio, and other file types)    |
  </div>
</div>

<Tip>
  For more information about supported field types, please refer to the [Input Fields documentation](/en/guides/workflow/node/start#input-field).
</Tip>

### Field Configuration Options

All input field types include: required, optional, and additional settings. You can set whether fields are required by checking the appropriate option.

| Setting                   | Name          | Description                                                             | Example                                                  |
| ------------------------- | ------------- | ----------------------------------------------------------------------- | -------------------------------------------------------- |
| Required Settings         | Variable Name | Internal system identifier, usually named using English and underscores | `user_email`                                             |
|                           | Display Name  | Interface display name, usually concise and readable text               | User Email                                               |
| Type-specific Settings    |               | Special requirements for different field types                          | Text field max length 100 characters                     |
| Additional Settings       | Default Value | Default value when user hasn't provided input                           | Number field defaults to 0, text field defaults to empty |
|                           | Placeholder   | Hint text displayed when input box is empty                             | "Please enter your email"                                |
|                           | Tooltip       | Explanatory text to guide user input, usually displayed on mouse hover  | "Please enter a valid email address"                     |
| Special Optional Settings |               | Additional setting options based on different field types               | Validation of email format                               |

After completing configuration, click the preview button in the upper right corner to browse the form preview interface. You can drag and adjust field groupings. If an exclamation mark appears, it indicates that the reference is invalid after moving.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=18b9dec017c99ef2b840b67ae89e2db9" alt="" data-og-width="1280" width="1280" data-og-height="331" height="331" data-path="images/knowledge-base/knowledge-pipeline-orchestration-15.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ba7bc7acf021068054aa59672bda6cf8 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=7a73feeec489b7a85a3e1b8f4ebbbdc0 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=bad3c79b0e264b80e843187dd79a37a4 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=346af10f86753028cbea3f81e2fb8c0d 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=1872deddb1b536099bc8d9e3a45d09ad 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-15.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=2f2ecd4637dadc245bdbbdc85f15cc00 2500w" />

***

## Step 5: Name the Knowledge Base

<img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=5cb2a533f62160cac72e6cc8e994c361" alt="Name Knowledge Base" data-og-width="1280" width="1280" data-og-height="336" height="336" data-path="images/knowledge-base/create-knowledge-pipeline-11.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=fa3147fb13b420acf24f2d269fde965b 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=761e1a5499dfa28e4e8660a180895527 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=4844cac6ca768a175aae58f9812c42d6 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=63d25b20fc112c5072c2b359800213d2 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6c85e192423f2c5d197c5a17a1a91516 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/create-knowledge-pipeline-11.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=3980f920d0fc5befac26f34f0b6c8e9f 2500w" />

By default, the knowledge base name will be "Untitled + number", permissions are set to "Only me", and the icon will be an orange book. If you import it from a DSL file, it will use the saved icon.

Edit knowledge base inforamtion by clicking **Settings** in the left panel and fill in the information below:

* **Name & Icon**\
  Pick a name for your knowledge base.\
  Choose an emoji, upload an image, or paste an image URL as the icon of this knowledge base.
* **Knowledge Description** Provide a brief description of your knowledge base. This helps the AI better understand and retrieve your data. If left empty, Dify will apply the default retrieval strategy.
* **Permissions**\
  Select the appropriate access permissions from the dropdown menu.

***

## Step 6: Testing

You're almost there! This is the final step of the knowledge pipeline orchestration.

After completing the orchestration, you need to validate all the configuration first. Then, do some running tests and confirm all the settings. Finally, publish the knowledge pipeline.

### Configuration Completeness Check

Before testing, it's recommended to check the completeness of your configuration to avoid test failures due to missing configurations.

Click the checklist button in the upper right corner, and the system will display any missing parts.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=9d1f9c1b5923e6af2c4acc12899c5320" alt="" data-og-width="884" width="884" data-og-height="916" height="916" data-path="images/knowledge-base/knowledge-pipeline-orchestration-16.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=bd3f207ba2496ef3e9b50d922b7f2cc3 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=def463b330ecd398929bfd59c25ac72f 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ac1adb435d2a73d9a05116961370f729 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=3e7e3b14a8f442f1468dc48c74794fb6 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f8c1a54174adc83d24459aaa86aa60e7 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-16.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=fa35c99b56ce8fc1c00779939fb64380 2500w" />

After completing all configurations, you can preview the knowledge base pipeline's operation through test runs, confirm that all settings are accurate, and then proceed with publishing.

### Test Run

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=04ac4d5c9fa83858b7c069c322909a3c" alt="" data-og-width="962" width="962" data-og-height="130" height="130" data-path="images/knowledge-base/knowledge-pipeline-orchestration-17.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=ed07f9f0d61ce4955c6a6afa1f4c8d7a 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=1dd5021c7762429f204981a02fb3b3fe 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=805236110b7e43fbe6f084737e78556f 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=d2b32c0758f96750b09be8daf9881f09 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=4859a157d39945aadc7aa7d10d753683 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-17.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=506c3044ead0b743773208e589891bdd 2500w" />

1. **Start Test**: Click the "Test Run" button in the upper right corner
2. **Import Test File**: Import files in the data source window that pops up on the right

<Warning>
  **Important Note**: For better debugging and observation, only one file upload is allowed per test run.
</Warning>

3. **Fill Parameters**: After successful import, fill in corresponding parameters according to the user input form you configured earlier
4. **Start Test Run**: Click next step to start testing the entire pipeline

During testing, you can access [History Logs](/en/guides/workflow/debug-and-preview/history-and-logs#application-run-history) (track all run records with timestamps, execution status, and input/output summaries) and [Variable Inspector](/en/guides/workflow/debug-and-preview/variable-inspect) (a dashboard at the bottom showing input/output data for each node to help identify issues and verify data flow) for efficient troubleshooting and error fixing.

<img src="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=2614d82ac575c4dfbda14ee4859177b3" alt="Testing Tools" data-og-width="1280" width="1280" data-og-height="674" height="674" data-path="images/knowledge-base/knowledge-pipeline-orchestration-18.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=280&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=23e31974b45fbef55615f61bda10ff1b 280w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=560&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=0b4fe8b91e1b2ab85375caea271db9d8 560w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=840&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=2767f7fc84d63517a915dad6021d0876 840w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=1100&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=f1107e95cb8b18b5a92cb2d6a97c65df 1100w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=1650&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=5dc61fb0bfe8940a6a95706b5d706d7f 1650w, https://mintcdn.com/dify-6c0370d8/y0OuaOVt1Ats0jeT/images/knowledge-base/knowledge-pipeline-orchestration-18.png?w=2500&fit=max&auto=format&n=y0OuaOVt1Ats0jeT&q=85&s=8d967f879888f5f64b49c937f1f4aa96 2500w" />

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/knowledge-base/knowledge-pipeline/knowledge-pipeline-orchestration.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)

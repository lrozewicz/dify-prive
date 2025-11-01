# Multilingual README

> This article introduces the file specifications for Dify plugins' multilingual READMEs and their display rule in Dify Marketplace.

You can create multilingual READMEs for your plugin, which will be displayed in [Dify Marketplace](https://marketplace.dify.ai) and other locations based on the user's preferred language.

### README **File Specifications**

| **Language**        | Required | Filename                    | Path                                                   | **Description**                                                  |
| :------------------ | :------- | :-------------------------- | :----------------------------------------------------- | :--------------------------------------------------------------- |
| **English**         | Yes      | `README.md`                 | Plugin root directory                                  | /                                                                |
| **Other Languages** | No       | `README_<language_code>.md` | In the `readme` folder under the plugin root directory | Currently supports Japanese, Portuguese, and Simplified Chinese. |

Here's an example of the directory structure:

```bash  theme={"system"}
...
├── main.py
├── manifest.yaml
├── readme
│   ├── README_ja_JP.md
│   ├── README_pt_BR.md
│   └── README_zh_Hans.md
├── README.md
...
```

### How Multilingual READMEs are Displayed **in Marketplace**

When your plugin has a README in the user's preferred language, the plugin's detail page in Dify Marketplace will display that language version of the README.

<img src="https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=a7c5c10ce618a56e3b74f972f171a942" alt="" data-og-width="2882" width="2882" data-og-height="1920" height="1920" data-path="images/plugin_details_page_en.jpeg" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=280&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=968d79c3cbe30a1453889d8d493bb1d6 280w, https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=560&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=0a3093c292a8505e6608dfdd9a7fd1e7 560w, https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=840&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=c738d695c6f2c712715e4ad0d6a0a9b5 840w, https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=1100&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=1cdb780d13d8363e4d28d689f338222c 1100w, https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=1650&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=b4dcf34cd8576c68d6d16aab4a95ac08 1650w, https://mintcdn.com/dify-6c0370d8/fW20SkOBxacYCkTW/images/plugin_details_page_en.jpeg?w=2500&fit=max&auto=format&n=fW20SkOBxacYCkTW&q=85&s=68e6f476ac9b53068d62c63df60101a4 2500w" />

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/plugin-dev-en/0411-multilingual-readme.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)

# Manage Model Credentials

## Introduction

You can add multiple credentials for a model provider's predefined and custom models, and easily switch between, delete, or modify these credentials.

Here are some scenarios where adding multiple credentials is particularly helpful:

* **Environment Isolation**: Configure separate model credentials for different environments, such as development, testing, and production. For example, use a rate-limited credential in the development environment for debugging, and a paid credential with stable performance and a sufficient quota in the production environment to ensure service quality.

* **Cost Optimization**: Add and switch between multiple credentials from different accounts or model providers to maximize the use of free or low-cost quotas, thereby reducing application development and operational costs.

* **Model Testing**: During model fine-tuning or iteration, you may create multiple model versions. By adding credentials for these different versions, you can quickly switch between them to test and evaluate their performance.

<Tip>
  You can also use multiple credentials to configure load balancing for a model. For more information, see [Configure Load Balancing](/en/guides/model-configuration/load-balancing).
</Tip>

## Procedure

<Tabs>
  <Tab title="Predefined Model">
    After installing a model provider and configuring the first credential, click **Config** in the upper-right corner to perform the following actions:

    * Add a new credential
    * Select a credential as the default for all predefined models
    * Edit a credential
    * Delete a credential

    <Note>
      If the default credential is deleted, you must manually specify a new one.
    </Note>

        <img src="https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=ceeac0a982d23694a84aca9bb6cd403a" alt="Manage credentials for predefined models" data-og-width="1538" width="1538" data-og-height="678" height="678" data-path="images/predefined_model_credential.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=280&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=c3a961de219bf20c476239957fddeb7a 280w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=560&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=051a4a95e0c7b19c85b4629294839c08 560w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=840&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=24f4f67196e6f84df96ea69f562f17d2 840w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=1100&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=c29df3acab25c5f0754e127f9ba21e4d 1100w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=1650&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=64bf4de0eb78a39dfa265d19ab386d3d 1650w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/predefined_model_credential.png?w=2500&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=14bd05781cc417315e3686c91583bf6c 2500w" />
  </Tab>

  <Tab title="Custom Model">
    ### Manage Credentials for a Single Custom Model

    After installing a model provider and adding a custom model, follow these steps:

    1. In the model list, click the corresponding **Config**.

    2. In the **Specify model credential** panel, click the default credential to open the credential list, then perform the following actions:

       * Add a new credential

       * Select a credential as the default for that custom model

       * Edit a credential

       * Delete a credential

    <Warning>
      If you delete the only credential for a custom model, the model will also be deleted.
    </Warning>

        <img src="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=8dbcf0d42fd2b24dc16ed428ed477f05" alt="Manage credentials for a single custom model" data-og-width="1328" width="1328" data-og-height="722" height="722" data-path="images/custom_model_credential.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=280&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=736bb29c0a120c4bbf44ded9260423cf 280w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=560&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=f4955cfdb66bae67daa48e7ce31aefb9 560w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=840&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=17435e4fdb5a79dc3510232a0458c77e 840w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=1100&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=c6ef0c338132c0926e4cb4f79e6eb065 1100w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=1650&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=4e16ef18349d93eb4d21ba97a28c7afe 1650w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential.png?w=2500&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=873c52bc5027055a6d7f9b9d71eab38b 2500w" />

    <Info>
      When you add a new custom model with a name and type identical to an existing custom model, the system will add the new credential to that existing model rather than creating a duplicate.
    </Info>

    ### Manage Credentials for All Custom Models

    You can click **Manage Credentials** to view, edit, or delete the credentials for all custom models.

        <img src="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=ea4d55f05de45cbfb29325d118911afe" alt="Manage credentials for all custom models" data-og-width="1528" width="1528" data-og-height="692" height="692" data-path="images/custom_model_credential_list.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=280&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=8f60b0369521085af80755ab82db1966 280w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=560&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=1df0d3399610a10a77f08a116186788b 560w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=840&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=76d116d305befbfd305595ef36cd358f 840w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=1100&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=427e5112372003ee0257bbf8ac047e58 1100w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=1650&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=ce57c3bd860a569ceee4797589d8429f 1650w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/custom_model_credential_list.png?w=2500&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=31460ec37e6e34f35a38a097060a55b6 2500w" />

    After a custom model is removed, its credentials will remain in the **Manage Credentials** list. When you click **Add Model**, the system will display all removed custom models whose credentials still exist, allowing you to quickly re-add them.

        <img src="https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=f9c936b22c58e33a454e276fc7123808" alt="Removed models displayed for quick re-add" data-og-width="1534" width="1534" data-og-height="564" height="564" data-path="images/removed_custom_model_re-add.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=280&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=a2cfc49da609639d98aa912a3aea881a 280w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=560&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=e4874ae526b6d3d5a3927f878d7bd2eb 560w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=840&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=271adcde7cafa68bcfbc5ac024e60285 840w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=1100&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=c102aa21570b1db982238fbb3356b60d 1100w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=1650&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=a60050a7f68d3591a7a8e0050146a849 1650w, https://mintcdn.com/dify-6c0370d8/DLsSss2CKEMuNxH2/images/removed_custom_model_re-add.png?w=2500&fit=max&auto=format&n=DLsSss2CKEMuNxH2&q=85&s=8d7ddb3ab7d9d3124fa86b4b27dec85c 2500w" />

    If you delete all credentials for a removed custom model from the **Manage Credentials** list, that model will no longer appear when you click **Add Model**.
  </Tab>
</Tabs>

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/model-configuration/manage-model-credential.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)

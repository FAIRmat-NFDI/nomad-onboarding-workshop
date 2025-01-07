# Uploading Data to NOMAD

NOMAD supports a wide range of data structuring when uploading files. It can function as simple cloud storage, like Google Drive, or handle highly structured data that complies with the FAIR principles.

To upload data, you need a NOMAD account. If you don't have one yet, follow [these quick steps](../Module2/M2_x_create_account.md) to create one.

## Uploading Your Files

1. Go to [nomad-lab.eu](https://nomad-lab.eu) and click **OPEN NOMAD** in the top right corner.

2. Click on the **PUBLISH** menu in the top left corner and select **Uploads**.

3. Click **CREATE A NEW UPLOAD**. A new page will open, and an upload ID will be automatically assigned near the red user icon. At this point, only you can see and access this upload.

3. Drag and drop your file(s) into the designated field, or click the blue button **DROP FILES HERE OR CLICK TO OPEN DIALOG** to select files from your computer.

🎉 Congratulations! You’ve made your first upload to NOMAD.

<div style="text-align: center;">
    <img src="images/upload_files.gif" alt="Upload Files" width="800">
</div>


??? note "What is an Upload in NOMAD?"
    An upload helps you organize your files. Think of an upload as a project folder: you can include multiple files and organize them into directories and subdirectories. The files in an upload are called **raw files**. NOMAD never modifies raw files; you can always access, add, remove, or reorganize them as needed.

## Managing Your Upload

Here are a few quick tips to manage your uploads in this page:

- **Rename Your Upload:** By default, your upload is named **"unnamed upload."** Click the **pen icon** to rename it, enter your desired name, and click **SAVE**.

- **Collaborate on Your Upload:** You can also share the upload with colleagues you select. For this, click **EDIT UPLOAD MEMBERS** to manage permissions. Use the search field to find a colleague’s name, assign a role (**Co-author** for read/write access, **Reviewer** for read-only), and click **SUBMIT**. To invite non-NOMAD users, click **INVITE NEW USER**. If you want to make the upload publicly available on NOMAD, check the box above **EDIT UPLOAD MEMBERS**.

<div style="text-align: center;">
    <img src="images/manage_uploads_edit_members.gif" alt="Manage Uploads" width="800">
</div>

## What Happens after Uploading a File to NOMAD?

Two scenarios can occur based on whether NOMAD **recognizes** your raw file(s):

1. **If NOMAD does not recognize the file(s)**, it acts as simple storage. You can preview common formats such as `.txt`, `.csv`, `.pdf`, `.png`, `.jpg`, and `.tiff`. Proprietary formats like `.xlsx` and `.docx` cannot be previewed.

2. **If NOMAD recognizes the file**, meaning that a built-in **parser** exists for the file you uploaded, the file will be processed according to a data schemas. It means that NOMAD reads the file, extracts data and organizes them based on the data schema which allows for generating visualizations, and analysis automations. This is common for simulation files since they follow standardized structures. Also a variety of experimental data organized in NeXus format (`.nxs` format), are recognized by NOMAD.

??? info "Which Raw Files are Recognized by NOMAD?"
    NOMAD supports a variety of raw file formats through built-in parsers that convert raw files into a common data format. The full list of supported formats can be found on the **ABOUT > Information** page of the NOMAD GUI, or by visiting [this link](https://nomad-lab.eu/prod/v1/gui/about/information){:target="_blank"}.

    For additional file formats, NOMAD can be customized by adding new parsers. This is done using **plug-ins**, which are Python packages that can be installed into a local NOMAD Oasis. More details on creating and adding parsers are available in the [How to Write a Parser guide](https://nomad-lab.eu/prod/v1/docs/howto/plugins/parsers.html){:target="_blank"}.



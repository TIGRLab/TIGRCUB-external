# XNAT

## Getting Access to our XNAT

**Web-Based**

Our XNAT database can be accessed using your web browser at [https://xnat.imaging-genetics.camh.ca](https://xnat.imaging-genetics.camh.ca).

If you do not yet have a username and password, please contact [tigrlab@camh.ca](mailto:tigrlab@camh.ca).

Please note **we currently support only Firefox, Google Chrome, and Safari**. Our users have had trouble with Internet Explorer and we do not recommend you use this browser.

## Layout Overview

### Home Page
---------

The home page of XNAT looks like this:

![](/_img/guide.xnat-home.jpg)

On the left is a list of **projects**. Each project contains a set of scans for a particular study. In studies where we are collecting data from multiple sites, the project name ends with a number (`01`, `03`, etc). You will only be given access to the projects that you are directly involved in, so this list might be very short.

![](/_img/guide.xnat-home-projects.jpg)

On the right is a list subjects with recent changes. For example, you should see your new data uploads at the top of this list.

You can **change your password** from the home page by clicking on your user name (hidden at the top):

![](/_img/guide.xnat-home-user.jpg")


### Data Organization
-----------------

XNAT has a simple data organization format:

+ Subject
    + Session
        + Series

Each subject represents a particular person, each session represents a particular visit to the MRI, and each series represents a particular MRI sequence run on that person.

We have elected not to use the sessions in XNAT, and therefore, **all session and subject names should be identical**. Much more on that issue in our 'naming' guide.

Let's look at the session for subject `SPN01_CMH_PHA_FBN0065`, a fBIRN phantom from the SPINS study, by clicking on it under 'Recent Data Activity':

![](/_img/guide.xnat-session.jpg)

The list at the bottom are all of the series contained within the current session.

At the side is a set of commands one can use to do manage the data, such as deleting bad files, renaming the subject and/or session, or downloading copies of the data.

Along the top, you can see that we are actually inside the session `SPN01_CMH_PHA_FBN0065` for subject `SPN01_CMH_PHA_FBN0065`. This is because we ask that all session and subject names match. If you click `SUBJECT: SPN01_CMH_PHA_FBN0065` at the top, you should see this:

![](/_img/guide.xnat-subject.jpg)

Which lists all of the sessions for this subject.

Here, you can also manage the data from the right hand sidebar (rename the subject, or delete the data).

**In our database, we want each subject to have only one session. This is covered in more detail in our naming guide. Therefore, this screen should only ever have one session in it.**


## Uploading

### Upload Overview
---------------

+ Use the [upload tool supplied by XNAT](#upload-using-tool), OR upload in your [web browser](#upload-using-web-browser) using the **alternative method**.
+ Go to prearchive, and review.
+ Ensure subject name and session name are correct (and the same).
+ Submit to the archive.
+ If required, create an appropriate resources folder to contain non-DICOM data, and upload that data seperately

### Upload Using Tool
-----------------

**Install upload assisstant 1.6.5 for your operating system:**

+ [windows 64 bit](ftp://ftp.nrg.wustl.edu/pub/xnat/UploadAssistant_windows-x64_1_6_5.exe)
+ [windows 32 bit](ftp://ftp.nrg.wustl.edu/pub/xnat/UploadAssistant_windows-x86_1_6_5.exe)
+ [mac osx](ftp://ftp.nrg.wustl.edu/pub/xnat/UploadAssistant_macos_1_6_5.dmg)
+ [debian](ftp://ftp.nrg.wustl.edu/pub/xnat/UploadAssistant_linux_1_6_5.deb)
+ [red hat](ftp://ftp.nrg.wustl.edu/pub/xnat/UploadAssistant_linux_1_6_5.rpm)

The XNAT upload tool will walk you through uploading your dicoms to our XNAT server step-by-step. It does not work with `.zip` archives, and can only work on the folders themselves. So you might need to unzip your archive on your computer before attempting to upload.

The tool will ask for your XNAT login and password, and then for the location of the folder you wish to upload. If you are trying to upload a bunch of difference scans, you can just select the top folder containing all of the data. The tool will figure out the exact structure of your DICOMs.

To ensure you are uploading the correct data, you will need to input the scan date, so make sure you have that on hand. If you annonymized the data by overwriting the scan date, you will need to input the new value you used (e.g., Jan 1st 1900).

This tool will allow you to select scans to include / exclude from your upload. Feel free to uncheck 'extra' files not required by the scanning protocol. For example, FA maps generated by the MRI, 'screen_saves', and other misc files not explicitly defined in the scanning protocol.

Finally, upload the data. It is a good idea to visit the prearchive / the archive to make sure all of your data arrived in the database safely (see below).

### Uploading Using Web Browser
---------------------------

To upload your DICOM data to our XNAT server, you first want to put all of the relevant DICOM folders for a single subject's session in a `.zip` file.  Then, from the home page's top bar, select `upload`, then `images`.

![](/_img/guide.xnat-upload-1.gif)

From the **upload image sessions** page, we want to select the alternative upload method. We find this works better with a wide variety of systems. The link to the alternative upload system is hidden at the bottom;

![](/_img/guide.xnat-upload-2.gif")


On this page, we want to select what project we are uploading the data to, set the destination to prearchive, and select the zip file containing the DICOMs. Please be patient at this stage, as the upload can take some time.

![](/_img/guide.xnat-upload-3.gif")

Now, we need to make sure the metadata for the upload is set correctly (particularly the subject and session names). These should be automatically generated correctly from the DICOM headers, but if a mistake is made at the scanner, you can correct it in XNAT. This is done from the prearchive. From the top bar, select `upload`, then `go to prearchive`.

![](/_img/guide.xnat-upload-4.gif")

This screen contains all pending scans. The metadata for this upload is visible in the top right hand corner. Any data here is NOT accessible from the main database and will not be analyzed by us. You must make sure this data is reviewed and archived so that it can be properly analyzed, by simply selecting a series and clicking `review and archive`:

![](/_img/guide.xnat-upload-5.gif")

Recall that, in our database, the subject and session name must match exactly and should follow our naming convention. You can do that here by either adding a new subject (if need be), adding / editing the session.

You can also edit other metadata such as date of birth, gender, or handedness (if required).


![](/_img/guide.xnat-upload-6.gif")

Finally, at the bottom, select `submit`. Your data should now be available in the archive and appear on the main page under 'recent data activity'.

### Uploading Non-DICOM Data
------------------------

If collected, extra datatypes (e.g., physiological or behavioural) data collected during the MRI scans need to be uploaded separately. Non-image uploads could also be technologist notes or QC .pdf files. These must be added to a subject's session, which should be done after the DICOM files have been uploaded.

XNAT keeps the data organized under each subject's session in `resources/` and `scans/`. The `scans/` folder holds all of the uploaded DICOM data, and the `resources/` folder contains everything else. Therefore, under resources, you can create folders as nessicary:

+ `resources/logs` -- participant log sheets (.xls, .csv, .pdf, etc.)
+ `resources/behav` -- behavioural data for fMRI experiments.
+ `resources/physio` -- physiological recordings collected during the MRI protocol.

To upload data to one of these folders:

+ From the subject page, click on the session.
+ Click 'Manage Files' on the right hand bar. You should see a list of the DICOM scans under scans/ and a resources/ folder (potentially with some contents).
+ To create a folder: Click `Add Folder`. Set `Level` to `resources` and set a name for `folder`. Click `Create`.
+ To upload data to this folder: Click `Upload Files`, `Level` should be `resources`, and `Folder` should be the desired folder. Click 'Browse' and attach the `.zip` file. Click `Upload`.
+ Click 'extract files to server'.

### Uploading using direct DICOM transfer
-------------------------------------

If your MR unit is set up to send data directly from the scanner over the Internet, you may try sending us your data via this method using the following:

+ XNAT Address: da55.pet.utoronto.ca
+ DICOM Port: 8104.
+ Calling & Called Title: XNAT

**If you opt to use this method, please do a test push of your data so we can ensure there are no issues receiving your participant data!**

### Upload Rules
------------

+ Ensure your raw DICOM scans for a given participant are in each in their own folder.
+ **Do not** include NIFTI or otherwise converted files in this package.
+ **Do not** include any pre-processed data from the scanner (e.g., motion corrected data, FA maps, etc.) These pollute the database and we can generate better images in post-processing.

## Downloading

Let's say we want to download the T1 weighted image, T2 weighted image, and FLAIR image, from a subject in the PACTMD study. This subject was scanned on the CAMH scanner. We're going to download the data from the first session of subject 0110004.

From the home page, we select the PACTMD study, the subject `PACTMD_CMH_0110004_01_01`, and then the first (and only) session for that subject:

![](#/_img/guide.xnat-go-to-subject.gif)

On the right hand bar, we select `download`, and then `download images`:

![](/_img/guide.xnat-dl-link.gif)

Here we select our output file type (`.zip`), the series we want (T1, T2, and FLAIR), and finally click download:

![](/_img/guide.xnat-dl-dicoms.gif")

The DICOM files selected will be in the archive saved to your computer. You might need a program to 'unzip' your data such as [WinZip](http://www.winzip.com) for Windows or [UnRarX](http://unrarx.en.softonic.com/mac) for Mac.

## TIGRLAB XNAT Naming Convention
----------------------

As a general rule, we want all of the information about a file (the project, subject, timepoint, and any other details) directly in the filenames of every file, so we can always determine where our data came from at a glance. In detail:

+ **project** : What experiment is this data associated with?
+ **site** : What scanner did this data come from?
+ **subject** : What unique individual is this data associated with?
+ **timepoint** : In multiple time-point studies, we want to know which time point this data is from (e.g., baseline, 6 month follow-up, etc.)
+ **repeat** : Sometimes, data quality is bad, and the participant needs to come back to collect more data for the same time point. Other times, the participant needs to go to the bathroom. Every time a participant renters the scanner for a particular time point, they get a new repeat number.

We also distinguish between human, special human, and non-human phantom data (objects scanned at each site to evaluate scanner performance). They all have different naming conventions.

**Participants**

+ `[STUDY]_[SITE]_[SUBJECT]_[TIMEPOINT]_[REPEAT]`
+ `SPN01_CMH_0009_01_01`
+ Your **site** is unique to your scanner. See the list of site codes below.
+ In XNAT, there should be exactly one session per subject and timepoint. To enter a second timepoint, create a new subject with the appropriate name (e.g., `SPN01_CMH_0009_02_01`).

**Special Participants: Human Phantoms / Test-Retest Repeats**

In some studies, special subjects are being acquired (for example, traveling human phantoms to test scanner reliability between sites, or test-retest repeat scans to assess signal variability within sites). We can mark these by inserting a letter code in front of the subject code:

+ `P` -- human phantom
+ `R` -- test-retest repeat scan

Naming is otherwise the same as for normal participants:

+ `[STUDY]_[SITE]_[SUBJECT]_[TIMEPOINT]_[REPEAT]`
+ `SPN01_CMH_P009_01_01`
+ `PRE04_ZHH_R3562_01_01`.

**Non-Human Phantoms**

+ `[STUDY]_[SITE]_PHA_[PHANTOM]_[TIMEPOINT]`
+ SPN01_CMH_PHA_ADN0001
+ Phantom scans should be run regularly, and their session names will be numeric ascending.
+ Our web-based data viewing system requires the date fields in the DICOM header be intact.

### Naming Examples
---------------

As an example of how the data is organized, imagine a (poorly designed) study with two subjects where we collect T1 and DTI data at baseline, prescribe one of them a drug, and then scan them again in one year. Recall that XNAT organizes data into a

+ Subject
    + Session
        + Series

format, but we want all of our subjects and sessions in XNAT to have the same names. The baseline data might look like this for subject one:

+ Subject 1 (`SPN01_CMH_0001_01_01`)
    + Session 1 (`SPN01_CMH_0001_01_01`)
        + Series 1 (Localizer)
        + Series 2 (T1)
        + Series 3 (DTI)

Subject two was scanned, but moved a lot during the DTI, so we can't analyze it. So we brought that person back for a repeat scan due to the bad acquisition, and name it like this:

+ Subject 2 (`SPN01_CMH_0002_01_01`)
    + Session 1 (`SPN01_CMH_0002_01_01`)
        + Series 1 (Localizer)
        + Series 2 (T1)
        + Series 3 (DTI -- bad, needs to be redone)
+ Subject 2 (`SPN01_CMH_0002_01_02`)
    + Session 2 (`SPN01_CMH_0002_01_02`)
        + Series 1 (Localizer)
        + Series 2 (DTI)

Finally, the 1 year follow up scans for the subjects would look like this:

+ Subject 1 (`SPN01_CMH_0001_02_01`)
    + Session 1 (`SPN01_CMH_0001_02_01`)
        + Series 1 (Localizer)
        + Series 2 (T1)
        + Series 3 (DTI)
+ Subject 2 (`SPN01_CMH_0002_02_01`)
    + Session 1 (`SPN01_CMH_0002_02_01`)
        + Series 1 (Localizer)
        + Series 2 (T1)
        + Series 3 (DTI)

### DICOM Header Requirements
-------------------------

The XNAT database will **automatically name your files** correctly so long as you make suresome information in the DICOM header is correct:

+ `(0008,0020)`, `(0008,0021)`, `(0008,0022)` -- Correct scan date.
+ `(0010,0010)` -- Patient Name (e.g., `PRE01_MRC_021_01_01`).
+ `(0010,0020)` -- Patient ID (e.g., `PRE01_MRC_021_01_01`).

`(0010,0010)` and `(0010,0020)` map onto the subject and session, respectively. During uploads, if these fields are correct, everything will end up in the proper place of the database.

Now, the data will be included alongside the DICOM images in future downloads.

### Site Codes
--------

**Sites**

|Site|Full Name                              |Assigned Projects |
|----|---------------------------------------|------------------|
|IWA |U Iowa College of Medicine             |PRE02             |
|MIN |U Minnesota                            |PRE03             |
|GRD |Grady Hospital                         |PRE04             |
|BRG |Borgess WMU School of Medicine         |PRE05             |
|CRY |Cherry Street                          |PRE06             |
|MAS |U Massachusetts                        |PRE07             |
|CTN |Creighton U                            |PRE08             |
|PCE |Peace Health                           |PRE09             |
|SFD |Stanford U                             |PRE10             |
|TXS |U Texas                                |PRE11             |
|MCH |U Michigan                             |PRE12             |
|NWN |Northwestern U                         |PRE14             |
|MRC |Maryland Psychiatric Research Center   |SPN03             |
|ZHH |Zucker Hillside Hospital               |SPN02             |
|PMC |Pittsburg Medical Center               |STOPPD04          |
|CMH |Centre for Addiction and Mental Health |Many              |
|TGH |Toronto General Hospital               |DTI01             |
|MAS |University of Massachusetts            |STOPPD02          |
|NKI |Nathan Kline Institute                 |STOPPD03          |

**Phantoms**

|Name|Full Name                                 |Studies       |
|----|------------------------------------------|--------------|
|ADN | ADNI Magphan phantom                     | PREXX, SPNXX |
|FBN | fBIRN phantom                            | SPNXX        |
|ACR | American college of radiologists phantom | PREXX        |



Users internal to the CAMH system can access our QC dashboard here:

+ [QC Monitor](http://srv-dashboard.camhres.ca/index)

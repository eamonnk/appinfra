------
Markdown File Naming Convention:
{SN}-{FullName}.md

Sample: 
01-Lesson Introduction.md

Markdown File Content:
1. Component seperator. Every markdown file is a single unit, you can add many components to same unit, use three dask(---) as the component seperator.
2. HTML content.
## {HTML display name}
xxx
3. Video Component.
## {Video display name}
### Video File: {video FullName}

Sample:
## Azure Media Services - Protecting your Media Content with AES Encryption
This week on Azure Friday Scott talks to Mingfei Yang about how Azure Media Services can use AES Encryption to protect your media content. From AES-128 Clear Key, Microsoft PlayReady, and Google Widevine you can protect your content on any platform and it's a lot easier than you'd think!  

---
## Video: Protecting your Media Content with AES Encryption
### Video File: Protecting_your_Media_Content_with_AES_Encryption.mp4

------
Assessment File Naming Convention:
{SN}-{Course num}_{module num}.assessment.md

Sample:
01-DEMO100xLib_Mod00.assessment.md

Assessment Content:
See Assessment_Template.md

------
Graphics/Images:
Upload all graphics to $/{COURSE}/Modules/Linked_Image_Files/, and use the relative path in markdown file. 
Example as below:
![publish changes](..\../Linked_Image_Files/UnitPublish.JPG "publish or discard changes" "how to publish an update")
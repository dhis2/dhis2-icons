# DHIS2 Icons
DHIS2 uses a enum of all icons to contain all the information about what icons are available and their descriptions and keywords. The dhis2-icon-tool.jar in this repository is a tool to validate the files and icon data to point out any inconsistensies, and to generate a list of items used in the java enum in DHIS2.

## Validate and generate icon and icon data
To run the application, follow these steps:

1. Make sure all icon files (SVGs) are present in ./icons
2. Make sure you have data for all icons in csv format in ./csv
    2.1 The format of the csv file should be: name, description, keyword1, keyword2, ..., keyword5
    2.2 This application was not built to be durable, so avoid any newlines in the data itself
3. run the command: java -jar dhis2-icon-tool.jar

When running the application, the csv data and files are compared to make sure there are no missing data or files. If everything checks out, the application will write the resulting list of items in the following file: ./output/IconEnum.txt

## Update DHIS2 Icons
When updating DHIS2 with new icons, follow these steps:
1. Add all icon files to dhis2/dhis2-support/dhis-support-system/src/main/resources/SVGs/
2. Use the IconEnum.txt and copy the content. Replace the list of enums found in dhis-2/dhis-api/src/main/java/org/hisp/dhis/icon/Icon.java

## Notes
Icons whose names starts with a digit, will be prefixed with an underscore, as enum items cannot start with digits in java. For example, the icon name 3g will be replaced with _3g. However, the keys used by clients to refrence icons will remain the same as the name, without the underscore.
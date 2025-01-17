## Create project name
```sh
mkdir PC805-ORU-Development && cd PC805-ORU-Development
```
## Create project sessions
```sh
mkdir -p 1_Introduction 2_Hardware_Development/{2.1_System_Architecture,2.2_Hardware_Specifications,2.3_Design_Documentation/{Schematics,PCB_Layout},2.4_Bill_of_Materials,2.5_Hardware_Testing_and_Validation/Test_Reports} 3_Software_Development/{3.1_Software_Architecture/Detailed_Design,3.2_Development_Environment,3.3_Software_Components/{M-Plane_Software,S-Plane_Software,C-Plane_Software},3.4_Software_Integration,3.5_Software_Testing_and_Validation/Test_Reports} 4_Deployment_and_Maintenance/{4.1_Deployment_Guide,4.2_Maintenance_Guide} 5_Appendices 6_References/{ORAN_Standards,Picocom_PC805_Documents} 7_Seminars/{Seminar_1,Seminar_2} 8_Plans 9_Meeting_Reports
```
## Create project guide files
```sh
touch 1_Introduction/{Project_Overview.md,Objectives.md,Scope.md,Document_Structure.md} 2_Hardware_Development/2.3_Design_Documentation/{Schematics/README.md,PCB_Layout/README.md} 2_Hardware_Development/2.5_Hardware_Testing_and_Validation/Test_Reports/README.md 3_Software_Development/3.1_Software_Architecture/{High-Level_Design.md,Module_Descriptions.md,Design_Guide.md,Detailed_Design/Design_Document_1.md,Detailed_Design/Design_Document_2.md} 3_Software_Development/3.2_Development_Environment/{Tools_and_Frameworks.md,Setup_Instructions.md,IDE_Configuration.md,Version_Control.md} 3_Software_Development/3.3_Software_Components/{M-Plane_Software/{M-Plane_Overview.md,M-Plane_API.md,M-Plane_Implementation.md},S-Plane_Software/{S-Plane_Overview.md,S-Plane_API.md,S-Plane_Implementation.md},C-Plane_Software/{C-Plane_Overview.md,C-Plane_API.md,C-Plane_Implementation.md}} 3_Software_Development/3.4_Software_Integration/{Integration_Plan.md,Integration_Testing.md,Continuous_Integration.md} 3_Software_Development/3.5_Software_Testing_and_Validation/{Checklist.md,Test_Reports/{CONF_Test_Report.md,IOT_Test_Report.md,PICO_Test_Report.md,GIGA_Test_Report.md,Unit_Test_Report.md,System_Test_Report.md,Performance_Test_Report.md}} 4_Deployment_and_Maintenance/4.1_Deployment_Guide/{Deployment_Strategy.md,Deployment_Steps.md,Environment_Setup.md,Rollback_Procedures.md} 4_Deployment_and_Maintenance/4.2_Maintenance_Guide/{Routine_Maintenance.md,Troubleshooting.md,Update_Procedures.md,Backup_and_Restore.md} 5_Appendices/{Glossary.md,Acronyms.md,References.md} 7_Seminars/Seminar_1/{Presentation.pdf,Notes.md} 7_Seminars/Seminar_2/README.md 8_Plans/{Project_Plan.md,Development_Plan.md,Testing_Plan.md} 9_Meeting_Reports/{Meeting_2024-07-01.md,Meeting_2024-07-15.md,Meeting_2024-07-29.md}
```
## commit project
```sh
git add .
git commit -m "Initial commit with project structure"
git push original main
```

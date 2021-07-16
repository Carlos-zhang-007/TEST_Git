## How to configure SWC with simulink

### 1. Configure the arxml file in ARTOP

1. creat PortInterface

![image-20210715165948350](.\pic\image-20210715165948350.png)

2. creat SwComponentTypes

![image-20210716093116393](.\pic\image-20210716093116393.png)

3. configure ToplevelComposition

![image-20210716093323451](.\pic\image-20210716093323451.png)

4. configure SwcImplementations

![image-20210716093517275](.\pic\image-20210716093517275.png)

5. configure related system arxml (EthSystem_4.1.1.arxml in this sample)

![image-20210716094016261](.\pic\image-20210716094016261.png)



### 2. import arxmal into matlab simulink

1. ar = arxml.importer({'AUTOSAR_Datatypes.arxml','BswMMode.arxml','EthSystem_4.1.1.arxml','SoftwareComponents.arxml'})
2. createComponentAsModel(ar, '/DemoApplication/SwComponentTypes/SWC_SimulinkTest','ModelPeriodicRunnablesAs','FunctionCallSubsystem')

![image-20210716094432877](.\pic\image-20210716094432877.png)

### 3. configure SWC in simulink

1. before configuring

![image-20210716094828113](.\pic\image-20210716094828113.png)

2. after configuring

![image-20210716094959616](.\pic\image-20210716094959616.png)

3. generate C code

![image-20210716095221521](.\pic\image-20210716095221521.png)



### 4. configure com and RTE in EB

1. import arxml into EB
2. configure com

![image-20210716101759021](.\pic\image-20210716101759021.png)

![image-20210716102826420](.\pic\image-20210716102826420.png)

3. configure RTE signal mapping

![image-20210716102209527](.\pic\image-20210716102209527.png)



### 5. integrate generated code into project

1. add generated SWC_SimulinkTest.c  file into /source/application folder.
2. replace include head file to Rte_SWC_SimulinkTest.h


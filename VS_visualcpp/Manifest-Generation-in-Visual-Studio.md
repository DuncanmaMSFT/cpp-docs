---
title: "Manifest Generation in Visual Studio"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
caps.latest.revision: 14
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Manifest Generation in Visual Studio
Generation of a manifest file for a particular project can be controlled in the project **Property Pages** dialog. On the **Configuration Properties** tab, click **Linker**, then **Manifest File**, then **Generate Manifest**. By default the project properties of new projects are set to generate a manifest file. However it is possible to disable generation of the manifest for a project using the **Generate Manifest** property of the project. When this property is set to **Yes**, the manifest for this project is generated. Otherwise the linker ignores assembly information when resolving dependencies of the application code, and does not generate the manifest.  
  
 The build system in Visual Studio allows the manifest to be embedded in the final binary application file, or generated as an external file. This behavior is controlled by the **Embed Manifest** option in the **Project Properties** dialog. To set this property, open the **Manifest Tool** node, then select **Input and Output**. If the manifest is not embedded, it is generated as an external file and saved in the same directory as the final binary. If the manifest is embedded, Visual Studio embeds the final manifests using the following process:  
  
1.  After the source code is compiled to object files, the linker collects dependent assembly information. While linking the final binary, the linker generates an intermediate manifest that is used later to generate the final manifest.  
  
2.  After the intermediate manifest and linking are finished, the manifest tool will be executed to merge a final manifest and save it as an external file.  
  
3.  The project build system then detects whether the manifest generated by the manifest tool contains different information than the manifest already embedded in the binary.  
  
4.  If the manifest embedded in the binary is different from the manifest generated by the manifest tool, or the binary does not contain an embedded manifest, Visual Studio will invoke the linker one more time to embed the external manifest file inside the binary as a resource.  
  
5.  If the manifest embedded in the binary is the same as the manifest generated by the manifest tool, the build will continue to the next build steps.  
  
 The manifest is embedded inside the final binary as a text resource and it can be viewed by opening the final binary as a file in Visual Studio. To ensure that the manifest points to the correct libraries, follow the steps described in [Understanding the Dependencies of a Visual C++ Application](../VS_visualcpp/Understanding-the-Dependencies-of-a-Visual-C---Application.md) or follow the suggestions described in the [Troubleshooting](../VS_visualcpp/Troubleshooting-C-C---Isolated-Applications-and-Side-by-side-Assemblies.md) section.  
  
## See Also  
 [How to: Embed a Manifest Inside a C/C++ Application](../VS_visualcpp/How-to--Embed-a-Manifest-Inside-a-C-C---Application.md)   
 [Private Assemblies](_win32_private_assemblies)   
 [Manifest Tool](http://msdn.microsoft.com/library/aa375649)   
 [Understanding Manifest Generation for C/C++ Programs](../VS_visualcpp/Understanding-Manifest-Generation-for-C-C---Programs.md)
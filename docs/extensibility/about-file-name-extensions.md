---
title: "О расширений имен файлов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "расширения файлов"
  - "расширения имен файлов"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# О расширений имен файлов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При регистрации расширение файла VSPackage, можно связать его с необходимой версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Это важно, если более чем одна версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливает на компьютере.  
  
 Расширения файлов для VSPackages зарегистрированы с ключом HKEY\_CLASSES\_ROOT со значением по умолчанию, указывающий на связанный обработчик действия идентификатору progid \(идентификатору progid\).  
  
 Ниже приведен пример данных о регистрации для расширения файлов .vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Файлы, связанные с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] иметь версию progid, например  `VisualStudio.vcproj.8.0`включение параллельная установка продукта для поддержания ассоциаций расширения файлов между версий продукта.  Идентификатор progid для конкретной версии также позволяет использовать стандартных команд, как открытый, правка и т д без вопросы, связанные с перезаписать или перезаписываться другими приложениями или версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 В некоторых случаях идентификатор progid, связанный с расширением файла не должен быть изменен.  Например, идентификатор progid для расширения файла .htm \(идентификатор progid\) \= htmlfile усилия код которого написан в нескольких местах в операционной системе и широко известен и используется совместно с файлами .htm и .html.  
  
## См. также  
 [Регистрация расширений файлов для развертываний Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
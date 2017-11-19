---
title: "По расширениям файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aba03fd68fc5e0e68dbf13887de0c25094fa951
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="about-file-name-extensions"></a>По расширениям файлов
При регистрации расширение файла VSPackage, ее необходимо связать с версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Это важно при более одной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлен на компьютере.  
  
 Расширения файлов для пакетов VSPackage регистрируются в разделе HKEY_CLASSES_ROOT со значением по умолчанию, который указывает связанный программный идентификатор (ProgID).  
  
 Ниже приведен пример регистрационной информации для расширения файла с расширением VCPROJ:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Файлы, связанные с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должен иметь ProgID с версиями, такие как `VisualStudio.vcproj.8.0`, чтобы разрешить установку side-by-side продукта для поддержания версии продуктов сопоставлений расширений файлов. Зависящие от версии идентификатор ProgID также позволяет использовать стандартные действия, такие как открытие, изменение и так далее, не заботиться о перезаписи или перезаписи других приложений и версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 В некоторых случаях программный идентификатор, связанный с расширением файла не должны изменяться. Например, идентификатор ProgID для расширения файла .htm (progid = htmlfile) закодирована в нескольких местах в операционной системе, а также является и широко используется в связи с .htm и HTML-файлах.  
  
## <a name="see-also"></a>См. также  
 [Регистрация расширения имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
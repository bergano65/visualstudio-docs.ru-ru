---
title: О расширениях имен файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148036"
---
# <a name="about-file-name-extensions"></a>Сведения о расширениях имен файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При регистрации расширения файла VSPackage его можно связать с версией [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Это важно, если [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] на компьютере установлено более одной версии.  
  
 Расширения файлов для пакетов VSPackage регистрируются в разделе HKEY_CLASSES_ROOT Key со значением по умолчанию, которое указывает на связанный программный идентификатор (ProgID).  
  
 Ниже приведен пример сведений о регистрации для расширения VCPROJ-файла.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Файлы, связанные с, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] должны иметь идентификатор ProgID, например `VisualStudio.vcproj.8.0` , чтобы обеспечить параллельную установку продукта для поддержки сопоставлений расширений файлов между версиями продуктов. Идентификатор ProgID, зависящий от версии, также позволяет использовать стандартные глаголы, такие как Open, Edit и т. д., без необходимости перезаписи или перезаписи другими приложениями или версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 В некоторых случаях не следует изменять идентификатор ProgID, связанный с расширением файла. Например, идентификатор ProgID для расширения файла htm (ProgID = хтмлфиле) жестко закодирован в ряде мест в операционной системе и широко известен и используется в связи с файлами htm и HTML.  
  
## <a name="see-also"></a>См. также:  
 [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

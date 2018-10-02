---
title: О расширения имен файлов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8a299d7b2470b16761e4a418e0717a91c2929e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572424"
---
# <a name="about-file-name-extensions"></a>Сведения о расширениях имен файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [о расширения имен файлов](https://docs.microsoft.com/visualstudio/extensibility/about-file-name-extensions).  
  
При регистрации расширением файла пакета VSPackage, связывается с версией [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Это важно Если более одной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] устанавливается на компьютере.  
  
 Расширения файлов для пакетов VSPackage, регистрируются в разделе HKEY_CLASSES_ROOT ключ со значением по умолчанию, который указывает на связанный программный идентификатор (ProgID).  
  
 Ниже приведен пример сведений о регистрации для расширения файла с расширением VCPROJ:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Файлы, связанные с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] должен иметь ProgID с версиями, такие как `VisualStudio.vcproj.8.0`, чтобы разрешить установку side-by-side продукта, чтобы поддерживать ассоциации расширений файлов для версий продукта. ProgID конкретной версии также можно использовать стандартные действия, например открытым, редактирование и т. д., не заботиться о перезаписи или перезаписи другими приложениями или версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 В некоторых случаях идентификатор ProgID, связанный с расширением файла не должен изменяться. Например, идентификатор ProgID для расширения .htm файла (progid = htmlfile) закодирована в нескольких местах в операционной системе, а также является и широко используется в связи с .htm и HTML-файлах.  
  
## <a name="see-also"></a>См. также  
 [Регистрация расширений имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)


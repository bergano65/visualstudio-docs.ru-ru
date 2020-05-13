---
title: О расширении имен файлов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740348"
---
# <a name="about-file-name-extensions"></a>О расширении имен файлов
При регистрации расширения файла VSPackage вы связываете [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]его с версией . Это важно, если на [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] компьютере установлена несколько версий.

 Расширения файлов для VSPackages регистрируются под **HKEY_CLASSES_ROOT** ключом со значением по умолчанию, которое указывает на связанный программный идентификатор (ProgID).

 В следующем примере показана регистрационная информация для расширения файла *.vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Файлы, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] связанные с должны иметь версию ProgID, такие как `VisualStudio.vcproj.8.0`. Версия ProgID позволяет бок о бок установки продукта для поддержания ассоциаций расширения файлов среди версий продукта. Специфическая версия ProgID также позволяет использовать стандартные глаголы, такие как открытые, отодевные и так далее, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]без заботы о перезаписи или перезаписи другими приложениями или версиями .

 В некоторых случаях ProgID, связанный с расширением файла, не должен быть изменен. Например, ProgID для расширения файла *.htm* (progid - htmlfile) жестко кодируется в ряде мест в операционной системе, и широко известен и используется в сотрудничестве с *файлами .htm* и *.html.*

## <a name="see-also"></a>См. также
- [Регистрация расширений имени файла для бок о бок развертывания](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Указать обработчики файлов для расширения имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

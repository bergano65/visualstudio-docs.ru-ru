---
title: О расширения имен файлов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60a721581c3deb4588df59974768c634c2e9515f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313721"
---
# <a name="about-file-name-extensions"></a>О расширения имен файлов
При регистрации расширением файла пакета VSPackage, связывается с версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Это важно Если более одной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливается на компьютере.

 Расширения файлов для пакетов VSPackage, зарегистрированные в разделе **HKEY_CLASSES_ROOT** ключа со значением по умолчанию, который указывает на связанный программный идентификатор (ProgID).

 В следующем примере показано сведения о регистрации для *.vcproj* расширение файла:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Файлы, связанные с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должен иметь ProgID с версиями, такие как `VisualStudio.vcproj.8.0`. С версиями ProgID позволяет side-by-side установок продукта, чтобы поддерживать ассоциации расширений файлов для версий продукта. ProgID конкретной версии также можно использовать стандартные действия, например открытым, редактирование и т. д., не заботиться о перезаписи или перезаписи другими приложениями или версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 В некоторых случаях идентификатор ProgID, связанный с расширением файла не должен изменяться. Например, идентификатор ProgID для *.htm* расширение файла (progid = htmlfile) является жестко в нескольких местах в операционной системе, которая и широко используется в связи с *.htm* и *.html* файлов.

## <a name="see-also"></a>См. также
- [Регистрация расширений имен файлов для развертываний side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Укажите обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
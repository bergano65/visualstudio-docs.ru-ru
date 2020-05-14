---
title: Указание обработчиков файлов для расширения имен файлов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699756"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Указание обработчиков файлов для расширений имен файлов
Существует несколько способов определения приложения, которое обрабатывает файл с определенным расширением файла. Глаголы OpenWithList и OpenWithProgids являются двумя способами указания обработчиков файлов под записью реестра для расширения файла.

## <a name="openwithlist-verb"></a>OpenWithList глагол
 При нажатии кнопки "Правой кнопки" в Windows Explorer вы видите **команду Open.** Если более одного продукта связано с расширением, вы видите **Open With** submenu.

 Вы можете зарегистрировать различные приложения, чтобы открыть расширение, установив ключ OpenWithList для расширения файла в HKEY_CLASSES_ROOT. Приложения, перечисленные в этом ключе для расширения файла, отображаются в **статье «Рекомендуемые программы»** в **поле Open With** dialog. В следующем примере показаны приложения, зарегистрированные для открытия расширения файла .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Ключи, указывающие заявки, из списка под HKEY_CLASSES_ROOT приложений.

 Добавляя ключ OpenWithList, вы заявляете, что приложение поддерживает расширение файла, даже если другое приложение берет на себя ответственность за расширение. Это может быть будущая версия приложения или другого приложения.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Программные идентификаторы (ProgID) являются дружественными версиями ClassID, которые идентифицируют версию приложения или объект COM. Каждый совместно созидаемый объект должен иметь свой собственный ProgID. Например, VisualStudio.DTE.7.1 запускает Visual Studio .NET 2003, в то [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]время как VisualStudio.DTE.10.0 начинается . Как владелец типа проекта или типа элемента проекта, необходимо создать для расширения файла специфический ProgID. Эти ProgIDs могут быть излишними в том, что более одного ProgID может начать то же приложение. Для получения дополнительной [Registering Verbs for File Name Extensions](../extensibility/registering-verbs-for-file-name-extensions.md)информации см.

 Используйте следующую конвенцию именования для версионных файлов ProgIDs, чтобы избежать дублирования с регистрацией от других поставщиков:

|Расширение файла|Версия ProgID|
|--------------------|----------------------|
|.расширение|Productname. extension.versionMajor.versionMinor|

 Вы можете зарегистрировать различные приложения, которые могут открыть определенное расширение файла, добавив\\версии ProgIDs в качестве значений для*\<расширения *HKEY_CLASSES_ROOT>ключом OpenWithProgids. Этот ключ реестра содержит список альтернативных ProgIDs, связанных с расширением файла. Приложения, связанные с перечисленными ProgIDs, отображаются в подменю **Open With**_Product Name._ Если одно и то же `OpenWithList` `OpenWithProgids` приложение указано как в ключах, так и в ключах, операционная система объединяет дубликаты.

> [!NOTE]
> Ключ `OpenWithProgids` поддерживается только в Windows XP. Поскольку другие операционные системы игнорируют этот ключ, не используйте его в качестве единственной регистрации для обработчиков файлов. Используйте этот ключ, чтобы обеспечить лучший пользовательский интерфейс Windows XP.

 Добавьте желаемые ProgID в качестве значений типа REG_NONE. Следующий код представляет собой пример регистрации ProgIDs для расширения файла (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 ProgID, указанный как значение по умолчанию для расширения файла, является обработчиком файлов по умолчанию. Если вы измените ProgID для расширения файла, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] который поставляется с предыдущей версией или которые `OpenWithProgids` могут быть переданы другим приложениям, то вы должны зарегистрировать ключ для расширения файла и указать новый ProgID в списке вместе со старыми ProgIDs вы поддерживаете. Пример:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Если старый ProgID имеет глаголы, связанные с ним, то эти глаголы также будут отображаться под **Open With** *Название продукта* в меню ярлыка.

## <a name="see-also"></a>См. также
- [Сведения о расширениях имен файлов](../extensibility/about-file-name-extensions.md)
- [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)

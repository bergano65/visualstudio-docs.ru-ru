---
title: "Новые возможности MSBuild 15 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: 23
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 620d5739c450ddece13257bf7efa249ebf9c2a6a
ms.lasthandoff: 03/07/2017

---
# <a name="whats-new-in-msbuild-15"></a>Новые возможности MSBuild 15
MSBuild теперь предоставляется в составе [основного пакета SDK .NET](https://www.microsoft.com/net/download/core). Проекты на базе .NET Core можно создавать в Windows, macOS и Linux.  

## <a name="changed-path"></a>Измененный путь
 Теперь MSBuild устанавливается в папку в пути установки каждой версии Visual Studio. Например, `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Для поиска MSBuild можно использовать следующий модуль PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Теперь MSBuild не регистрируется в глобальном кэше сборок. Чтобы обратиться к MSBuild программным образом, используйте пакеты NuGet.

## <a name="changed-properties"></a>Измененные свойства  
 В связи с выходом нового номера версии изменены следующие свойства MSBuild.  

-   `MSBuildToolsVersion` для этой версии средств имеет значение 15.0. Версия сборки имеет значение 15.1.0.0.

-   `MSBuildToolsPath` теперь не имеет фиксированного расположения. По умолчанию он находится в папке MSBuild\15.0\Bin относительно папки установки Visual Studio, но место размещения Visual Studio можно изменить во время установки.

-   Значения `ToolsVersion` теперь не сохраняются в реестре.  

-   Свойства `SDK35ToolsPath` и `SDK40ToolsPath` указывают на пакет SDK для платформы .NET Framework, поставляемый с соответствующей версией Visual Studio (например, 10.0A для инструментов 4.X).  

## <a name="updates"></a>Обновления
- В элемент [Project](../msbuild/project-element-msbuild.md) добавлен новый атрибут `SDK`. Также атрибут `Xmlns` стал необязательным.
- Для внешних целевых объектов элемента [Item](../msbuild/item-element-msbuild.md) добавлен новый атрибут `Update`. Кроме того, снято ограничение на атрибут `Remove`.
- `Directory.Build.props` является определяемым пользователем файлом, который содержит настройки для проектов в каталоге. Этот файл автоматически импортируется из Microsoft.Common.targets, если свойству `ImportDirectoryBuildTargets` не задано значение **false**. Microsoft.Common.targets импортирует `Directory.Build.targets`.
- Все метаданные с именами, которые не противоречат текущему списку атрибутов, можно по желанию разработчика выразить в виде атрибута. Дополнительные сведения см. в статье [Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Новые функции свойств

- `EnsureTrailingSlash` добавляет завершающую косую черту к пути, если она отсутствует.
- `NormalizePath` объединяет элементы пути и проверяет, что выходная строка имеет правильные знаки разделения для каталогов, используемые в текущей операционной системе.
- `NormalizeDirectory` объединяет элементы пути, добавляет косую черту при необходимости и проверяет, что выходная строка имеет правильные знаки разделения для каталогов, используемые в текущей операционной системе.
- `GetPathOfFileAbove` возвращает путь к файлу, непосредственно предшествующему данному. Она функционально эквивалентна вызову такой инструкции: `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>См. также
[MSBuild](../msbuild/msbuild.md)


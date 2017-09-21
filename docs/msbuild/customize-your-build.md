---
title: "Настройка сборки | Документы Майкрософт"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: ru-ru
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Настройка сборки
Чтобы указать новое настраиваемое свойство для проектов в решении, в версиях MSBuild, предшествующих версии 15, приходилось вручную добавлять ссылку на это свойство в каждый файл проекта в решении. Либо приходилось определять свойство в файле PROPS и затем явно импортировать файл PROPS в каждый проект в решении.

Однако теперь можно добавить новое свойство в каждый проект за один шаг, определив его в единственном файле Directory.Build.props в корне репозитория. При запуске MSBuild Microsoft.Common.props ищет файл Directory.Build.props в структуре каталогов (а Microsoft.Common.targets ищет Directory.Build.targets). Если он его находит, то импортирует свойство. Directory.Build.props является определяемым пользователем файлом, который содержит настройки для проектов в каталоге.

## <a name="directorybuildprops-example"></a>Пример Directory.Build.props
Например, если нужно разрешить всем проектам доступ к новой функции Roslyn **/deterministic** (предоставляемой свойством `$(Deterministic)` в целевом объекте Roslyn CoreCompile), можно сделать следующее:

1. Создайте в корне репозитория файл с именем Directory.Build.props.
2. Добавьте в этот файл приведенный ниже XML-код.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Запустите MSBuild. Существующие импорты Microsoft.Common.props и Microsoft.Common.targets в проекте находят файл и импортируют его.

## <a name="search-scope"></a>Область поиска
При поиске файла Directory.Build.props MSBuild обходит структуру каталогов вверх от расположения проекта ($(MSBuildProjectFullPath)), а после его нахождения останавливается. Например, если ваш $(MSBuildProjectFullPath) имел значение c:\users\username\code\test\case1, MSBuild начнет поиск там, а затем будет переходить вверх по структуре каталогов, пока не найдет файл Directory.Build.props file, как показано в следующей структуре каталогов.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
Расположение файла решения не зависит от Directory.Build.props.

## <a name="import-order"></a>Порядок импорта

Directory.Build.props импортируется в Microsoft.Common.props очень рано, и определенные позднее свойства ему недоступны. Поэтому не ссылайтесь на свойства, которые еще не определены (и в связи с этим оцениваются как пустые).

Directory.Build.targets импортируется из Microsoft.Common.targets после импорта файлов TARGETS из пакетов NuGet. Таким образом, его можно использовать для переопределения свойств и целевых объектов, определенных в большей части логики сборки, когда может потребоваться настройка файла проекта после окончательного импорта.

## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   


---
title: Настройка сборки | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dae51959313a7108c54466dff08b3641525818cd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="customize-your-build"></a>Настройка сборки
Чтобы указать новое настраиваемое свойство для проектов в решении, в версиях MSBuild, предшествующих версии 15, приходилось вручную добавлять ссылку на это свойство в каждый файл проекта в решении. Либо приходилось определять свойство в файле *.props* и затем явно импортировать файл *.props* в каждый проект решения.

Но теперь вы можете добавить новое свойство в любой проект за один шаг, определив его в единственном файле *Directory.Build.props* в корне репозитория. При запуске MSBuild *Microsoft.Common.props* ищет файл *Directory.Build.props* в структуре каталогов (а *Microsoft.Common.targets* ищет файл *Directory.Build.targets*). Если он его находит, то импортирует свойство. Пользовательский файл *Directory.Build.props* содержит настройки персонализации для проектов в своем каталоге.

## <a name="directorybuildprops-example"></a>Пример Directory.Build.props
Например, если вы хотите предоставить всем проектам новую функцию Roslyn **/deterministic** через свойство `$(Deterministic)` в целевом объекте Roslyn `CoreCompile`, можно сделать следующее.

1. Создайте в корне репозитория файл с именем *Directory.Build.props*.
2. Добавьте в этот файл приведенный ниже XML-код.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Запустите MSBuild. Уже существующие в проекте файлы импорта *Microsoft.Common.props* и *Microsoft.Common.targets* находят новый файл и импортируют его.

## <a name="search-scope"></a>Область поиска
При поиске файла *Directory.Build.props* MSBuild обходит структуру каталогов вверх от расположения проекта (`$(MSBuildProjectFullPath)`). Когда файл найден, поиск останавливается. Например, если `$(MSBuildProjectFullPath)` имеет значение *c:\users\username\code\test\case1*, MSBuild начнет поиск там, а затем будет переходить вверх по структуре каталогов, пока не найдет файл *Directory.Build.props*. Пример такого поиска по структуре каталогов представлен ниже.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
Расположение файла решения не имеет значения для *Directory.Build.props*.

## <a name="import-order"></a>Порядок импорта

*Directory.Build.props* импортируется в *Microsoft.Common.props* очень рано, поэтому определенные позднее свойства ему недоступны. Поэтому не ссылайтесь на свойства, которые еще не определены (и в связи с этим оцениваются как пустые).

*Directory.Build.targets* импортируется из *Microsoft.Common.targets* после импорта файлов *.targets* из пакетов NuGet. Таким образом, его можно использовать для переопределения свойств и целевых объектов, определенных в большей части логики сборки, когда может потребоваться настройка файла проекта после окончательного импорта.

## <a name="use-case-multi-level-merging"></a>Вариант использования: многоуровневое слияние

Предположим, что вы используете следующую стандартную структуру решения:

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

Допустим, вам нужны некоторые общие свойства для всех проектов *(1)*, а также общие свойства для проектов *исходного кода* *(2-src)* и общие свойства для проектов *тестирования* *(2-test)*.

Чтобы система MSBuild правильно объединила "внутренние" файлы (*2-src* и *2-test*) с "внешними" (*1*), обязательно учитывайте, что MSBuild прекращает сканирование при обнаружении файла *Directory.Build.props*. Чтобы продолжить его и включить в слияние внешний файл, добавьте в оба внутренних файла следующее:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Ниже кратко описан основной алгоритм работы MSBuild.

- Для каждого проекта MSBuild находит ближайший файл *Directory.Build.props*, расположенный выше в структуре решения, объединяет его с параметрами по умолчанию и на этом останавливает сканирование.
- Если вы хотите обнаружить и объединить несколько уровней, импортируйте "внешний" файл из "внутреннего", как показано выше ([`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove)).
- Если "внешний" файл сам не импортирует ничего, расположенного выше, то сканирование останавливается здесь.
- Для управления процессом сканирования и слияния используйте `$(DirectoryBuildPropsPath)` и `$(ImportDirectoryBuildProps)`.

Проще говоря, MSBuild останавливает поиск на первом файле *Directory.Build.props*, который ничего не импортирует.

## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   

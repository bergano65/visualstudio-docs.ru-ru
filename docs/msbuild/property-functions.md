---
title: Функции свойств | Документы Майкрософт
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7e8c3bab691eeaf71383aef3315b51173492f7
ms.sourcegitcommit: 2dc924c96a6d48803c8eedc3d6781202629b41fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "57737031"
---
# <a name="property-functions"></a>Функции свойств

В версиях 4 и 4.5 платформы .NET Framework можно оценивать скрипты MSBuild с помощью функции свойства. Функции свойства можно использовать во всех случаях, где появляются свойства. В отличие от задач, функции свойства можно использовать за пределами целей и оценивать до запуска целей.

 Без использования задач MSBuild вы можете читать системное время, сравнивать строки, сопоставлять регулярные выражения и выполнять другие действия в скрипте построения. MSBuild попытается преобразовать строку в число и число в строку и при необходимости выполнит другие преобразования.

## <a name="property-function-syntax"></a>Синтаксис функции свойства

Существуют три типа функций свойства, каждая из которых имеет свой синтаксис.

- Функции свойства строки (экземпляра)
- Функции статичного свойства
- Функции свойства MSBuild

### <a name="string-property-functions"></a>Функции свойства строки

Все значения свойства построения являются значениями строки. Для управления значением свойства можно использовать методы строки (экземпляра). Например, можно извлечь имя диска (первые три символа) из свойства построения, которое представляет собой полный путь, с помощью следующего кода.

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Функции статичного свойства

В скрипте построения можно получить доступ к статическим свойствам и методам многих системных классов. Чтобы получить значение статического свойства, используйте следующий синтаксис, где \<Class> — это имя системного класса, а \<Property> — это имя свойства.

```fundamental
$([Class]::Property)
```

Например, чтобы задать свойство построения на текущую дату и время, можно использовать следующий код.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Чтобы вызвать статический метод, используйте следующий синтаксис, где \<Class> — это имя системного класса, \<Method> — имя метода, а (\<Parameters)> — список параметров метода.

```fundamental
$([Class]::Method(Parameters))
```

Например, чтобы задать свойство построения на новый GUID, можно использовать следующий скрипт.

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

В функциях статического свойства можно использовать любой статический метод или свойство следующих системных классов.

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Кроме этого, можно использовать следующие статические методы и свойства.

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Вызов методов экземпляра для статических свойств

При доступе к статическому свойству, которое возвращает экземпляр объектов, можно вызывать методы экземпляра этого объекта. Чтобы вызвать метод экземпляра, используйте следующий синтаксис, где \<Class> — это имя системного класса, \<Property> — имя свойства, \<Method> — это имя метода, а (\<Parameters>) — список параметров метода.

```fundamental
$([Class]::Property.Method(Parameters))
```

Имя класса должно содержать полное пространство имен.

Например, чтобы задать свойство построения на текущую дату, можно использовать следующий код.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Функции свойства MSBuild

Для обеспечения арифметической побитовой логической поддержки escape-символов можно использовать несколько статических методов из вашего построения. Получить доступ к этим методам можно с помощью следующего синтаксиса, где \<Method> — это имя метода, а (\<Parameters>) — список параметров метода.

```fundamental
$([MSBuild]::Method(Parameters))
```

Например, чтобы добавить два свойства с числовыми значениями, используйте следующий код.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Приведем список функций свойства MSBuild.

|Сигнатура функции|Описание|
|------------------------|-----------------|
|Сложение double(double a, double b)|Сложение двух значений double.|
|Сложение long(long a, long b)|Сложение двух значений long.|
|Вычитание double(double a, double b)|Вычитание двух значений double.|
|Вычитание long(long a, long b)|Вычитание двух значений long.|
|Умножение double(double a, double b)|Умножение двух значений double.|
|Умножение long(long a, long b)|Умножение двух значений long.|
|Деление double(double a, double b)|Деление двух значений double.|
|Деление long(long a, long b)|Деление двух значений long.|
|Остаток от деления double (double a, double b)|Остаток от деления двух значений double.|
|Остаток от деления long(long a, long b)|Остаток от деления двух значений long.|
|строка Escape (строка не экранируется)|Escape-последовательность строки в соответствии с правилами экранирования MSBuild.|
|строка Unescape (строка экранируется)|Unescape-последовательность строки в соответствии с правилами экранирования MSBuild.|
|Целое значение BitwiseOr(первое целое значение, второе целое значение)|Примените побитовый параметр `OR` к первому и второму значению (первое &#124; второе).|
|Целое значение BitwiseAnd(первое целое значение, второе целое значение)|Примените побитовый параметр `AND` к первому и второму значению (первое & второе).|
|Целое значение BitwiseXor(первое целое значение, второе целое значение)|Примените побитовый параметр `XOR` к первому и второму значению (первое ^ второе).|
|Целое значение BitwiseNot(первое целое значение)|Примените побитовый параметр `NOT` (~первое значение).|
|bool IsOsPlatform(строка platformString)|Указание того, является ли текущая платформа ОС `platformString`. `platformString` должен быть элементом <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|Значение true, если текущая операционная система — это система Unix.|
|Строка NormalizePath(параметры строка[] путь)|Возвращает канонический полный путь для предоставленного пути и проверяет правильность знаков разделения для каталогов, используемых в текущей операционной системе.|
|Строка NormalizeDirectory(параметры строка[] путь)|Возвращает канонический полный путь для предоставленного каталога и проверяет правильность знаков разделения для каталогов, используемых в текущей операционной системе, а также наличие косой черты в конце.|
|Строка EnsureTrailingSlash(строка путь)|Если в конце заданного пути нет косой черты, она добавляется. Если путь является пустой строкой, он не изменяется.|
|Строка GetPathOfFileAbove(строка файл, строка startingDirectory)|Поиск файла в зависимости от расположения текущего файла сборки, или на основе `startingDirectory`, если он указан.|
|GetDirectoryNameOfFileAbove(строка startingDirectory, строка fileName)|Поиск файла в указанном каталоге либо в структуре каталогов над ним.|
|Строка MakeRelative(строка basePath, строка путь)|Делает `path` относительным для `basePath`. `basePath` должен быть абсолютным каталогом. Если `path` невозможно сделать относительным, он возвращается дословно. Аналогично `Uri.MakeRelativeUri`.|
|Строка ValueOrDefault(стока conditionValue, строка defaultValue)|Возвращение строки в параметре "defaultValue" только в том случае, если параметр "conditionValue" пуст; в противном случае возвращается значение conditionValue.|

##  <a name="nested-property-functions"></a>Вложенные функции свойства

Функции свойства можно объединять для формирования более сложных функций, как показано в следующем примере.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

В этом примере возвращается значение <xref:System.IO.FileAttributes>`Archive` бит (32 или 0) файла, указанного в пути `tempFile`. Обратите внимание, что значения перечисляемых данных не могут отображаться в функциях свойства по имени. Вместо этого необходимо использовать числовое значение (32).

Во вложенных функциях свойства могут также появляться метаданные. Дополнительные сведения см. в статье [Пакетная обработка](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Функция свойства `DoesTaskHostExist` в MSBuild возвращает сведения об установленном сервере задач для указанной среды выполнения и значение архитектуры.

Эта функция свойства использует следующий синтаксис.

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

Функция свойства `EnsureTrailingSlash` в MSBuild добавляет косую черту, если таковая отсутствует.

Эта функция свойства использует следующий синтаксис.

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

Функция свойства `GetDirectoryNameOfFileAbove` в MSBuild выполняет поиск файла в каталогах выше текущего каталога в пути.

 Эта функция свойства использует следующий синтаксис.

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 В следующем коде показан пример этого синтаксиса.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

Функция свойства `GetPathOfFileAbove` в MSBuild возвращает путь к файлу, непосредственно предшествующему данному. Она функционально эквивалентна вызову.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Эта функция свойства использует следующий синтаксис.

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

Функция свойства `GetRegistryValue` в MSBuild возвращает значение раздела реестра. Она принимает два аргумента — имя раздела и имя значения — и возвращает значение в реестр. Если не указано имя значения, возвращается значение по умолчанию.

В следующих примерах показано, как используется эта функция.

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Функция свойства `GetRegistryValueFromView` в MSBuild получает данные системного реестра с учетом раздела реестра, значения и одного или нескольких упорядоченных представлений реестра. Раздел и значения ищутся в каждом представлении реестра по порядку, пока не будут найдены.

Синтаксис функции свойства.

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

64-разрядная операционная система Windows ведет раздел реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node**, содержащий представление реестра **HKEY_LOCAL_MACHINE\SOFTWARE** для 32-разрядных приложений.

По умолчанию 32-разрядное приложение, работающее на WOW64, получает доступ к 32-разрядному представлению реестра, а 64-разрядное приложение — к 64-разрядному представлению реестра.

Доступны следующие представления реестра.

|Представление реестра|Определение|
|-------------------|----------------|
|RegistryView.Registry32|Представление реестра для 32-разрядного приложения.|
|RegistryView.Registry64|Представление реестра для 64-разрядного приложения.|
|RegistryView.Default|Представление реестра, совпадающее с процессом, на котором работает приложение.|

Пример.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

В этом примере данные **SLRuntimeInstallPath** получаются из раздела **ReferenceAssemblies**, но сначала поиск выполняется в 64-разрядном представлении реестра, а затем — в 32-разрядном.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Функция свойства `MakeRelative` в MSBuild возвращает путь второго пути относительно первого пути. Каждый путь может быть файлом или папкой.

Эта функция свойства использует следующий синтаксис.

```fundamental
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

В следующем коде показан пример этого синтаксиса.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

Функция свойства `ValueOrDefault` в MSBuild возвращает первый аргумент, если он не нулевой или пустой. Если первый аргумент нулевой, функция возвращает второй аргумент.

В следующем примере показано, как используется эта функция.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="see-also"></a>См. также

- [Свойства MSBuild](../msbuild/msbuild-properties.md)

- [Общие сведения о MSBuild](../msbuild/msbuild.md)

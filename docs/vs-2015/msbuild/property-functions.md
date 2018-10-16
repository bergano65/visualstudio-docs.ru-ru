---
title: Функции свойств | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bed1496eb5519b315d2a52e500cb9cfd916fa248
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250514"
---
# <a name="property-functions"></a>Функции свойств
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В версиях 4 и 4.5 платформы .NET Framework можно оценивать скрипты MSBuild с помощью функции свойства. Функции свойства можно использовать во всех случаях, где появляются свойства. В отличие от задач, функции свойства можно использовать за пределами целей и оценивать до запуска целей.  
  
 Без использования задач MSBuild вы можете читать системное время, сравнивать строки, сопоставлять регулярные выражения и выполнять другие действия в скрипте построения. MSBuild попытается преобразовать строку в число и число в строку и при необходимости выполнит другие преобразования.  
  
 **Содержание раздела**  
  
-   [Синтаксис функции свойства](#BKMK_Syntax)  
  
    -   [Функции свойства строки](#BKMK_String)  
  
    -   [Функции статического свойства](#BKMK_Static)  
  
    -   [Вызов методов экземпляра в статических свойствах](#BKMK_InstanceMethods)  
  
    -   [Функции свойства MSBuild](#BKMK_PropertyFunctions)  
  
-   [Вложенные функции свойства](#BKMK_Nested)  
  
-   [MSBuild DoesTaskHostExist](#BKMK_DoesTaskHostExist)  
  
-   [MSBuild GetDirectoryNameOfFileAbove](#BKMK_GetDirectoryNameOfFileAbove)  
  
-   [MSBuild GetRegistryValue](#BKMK_GetRegistryValue)  
  
-   [MSBuild GetRegistryValueFromView](#BKMK_GetRegistryValueFromView)  
  
-   [MSBuild MakeRelative](#BKMK_MakeRelative)  
  
-   [MSBuild ValueOrDefault](#BKMK_ValueOrDefault)  
  
##  <a name="BKMK_Syntax"></a> Синтаксис функции свойства  
 Существуют три типа функций свойства, каждая из которых имеет свой синтаксис.  
  
-   Функции свойства строки (экземпляра)  
  
-   Функции статичного свойства  
  
-   Функции свойства MSBuild  
  
###  <a name="BKMK_String"></a> Функции свойства строки  
 Все значения свойства построения являются значениями строки. Для управления значением свойства можно использовать методы строки (экземпляра). Например, можно извлечь имя диска (первые три символа) из свойства построения, которое представляет собой полный путь, с помощью следующего кода.  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
###  <a name="BKMK_Static"></a> Функции статического свойства  
 В скрипте построения можно получить доступ к статическим свойствам и методам многих системных классов. Чтобы получить значение статического свойства, используйте следующий синтаксис, где *Class* — это имя системного класса, а *Property* — это имя свойства.  
  
 `$([Class]::Property)`  
  
 Например, чтобы задать свойство построения на текущую дату и время, можно использовать следующий код.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Чтобы вызвать статический метод, используйте следующий синтаксис, где *Class* — это имя системного класса, *Method* — это имя метода, а *(Parameters)* — это список параметров метода.  
  
 `$([Class]::Method(Parameters))`  
  
 Например, чтобы задать свойство построения на новый GUID, можно использовать следующий скрипт.  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 В функциях статического свойства можно использовать любой статический метод или свойство следующих системных классов.  
  
-   System.Byte  
  
-   System.Char  
  
-   System.Convert  
  
-   System.DateTime  
  
-   System.Decimal  
  
-   System.Double  
  
-   System.Enum  
  
-   System.Guid  
  
-   System.Int16  
  
-   System.Int32  
  
-   System.Int64  
  
-   System.IO.Path  
  
-   System.Math  
  
-   System.UInt16  
  
-   System.UInt32  
  
-   System.UInt64  
  
-   System.SByte  
  
-   System.Single  
  
-   System.String  
  
-   System.StringComparer  
  
-   System.TimeSpan  
  
-   System.Text.RegularExpressions.Regex  
  
-   Microsoft.Build.Utilities.ToolLocationHelper  
  
 Кроме этого, можно использовать следующие статические методы и свойства.  
  
-   System.Environment::CommandLine  
  
-   System.Environment::ExpandEnvironmentVariables  
  
-   System.Environment::GetEnvironmentVariable  
  
-   System.Environment::GetEnvironmentVariables  
  
-   System.Environment::GetFolderPath  
  
-   System.Environment::GetLogicalDrives  
  
-   System.IO.Directory::GetDirectories  
  
-   System.IO.Directory::GetFiles  
  
-   System.IO.Directory::GetLastAccessTime  
  
-   System.IO.Directory::GetLastWriteTime  
  
-   System.IO.Directory::GetParent  
  
-   System.IO.File::Exists  
  
-   System.IO.File::GetCreationTime  
  
-   System.IO.File::GetAttributes  
  
-   System.IO.File::GetLastAccessTime  
  
-   System.IO.File::GetLastWriteTime  
  
-   System.IO.File::ReadAllText  
  
###  <a name="BKMK_InstanceMethods"></a> Вызов методов экземпляра в статических свойствах  
 При доступе к статическому свойству, которое возвращает экземпляр объектов, можно вызывать методы экземпляра этого объекта. Чтобы вызвать метод экземпляра, используйте следующий синтаксис, где *Class* — это имя системного класса, *Property* — это имя свойства, *Method* — это имя метода, а *(Parameters)* — это список параметров метода.  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Имя класса должно содержать полное пространство имен.  
  
 Например, чтобы задать свойство построения на текущую дату, можно использовать следующий код.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
###  <a name="BKMK_PropertyFunctions"></a> Функции свойства MSBuild  
 Для обеспечения арифметической побитовой логической поддержки escape-символов можно использовать несколько статических методов из вашего построения. Получить доступ к этим методам можно с помощью следующего синтаксиса, где *Method* — это имя метода, а *Parameters* — это список параметров метода.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Например, чтобы добавить два свойства с числовыми значениями, используйте следующий код.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
 Приведем список функций свойства MSBuild.  
  
|Подпись функции|Описание|  
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
  
##  <a name="BKMK_Nested"></a> Вложенные функции свойства  
 Функции свойства можно объединять для формирования более сложных функций, как показано в следующем примере.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 В этом примере возвращается значение <xref:System.IO.FileAttributes>`Archive` бит (32 или 0) файла, указанного в пути `tempFile`. Обратите внимание, что значения перечисляемых данных не могут отображаться в функциях свойства по имени. Вместо этого необходимо использовать числовое значение (32).  
  
 Во вложенных функциях свойства могут также появляться метаданные. Дополнительные сведения см. в статье [Пакетная обработка](../msbuild/msbuild-batching.md).  
  
##  <a name="BKMK_DoesTaskHostExist"></a> MSBuild DoesTaskHostExist  
 Функция свойства `DoesTaskHostExist` в MSBuild возвращает сведения об установленном сервере задач для указанной среды выполнения и значение архитектуры.  
  
 Эта функция свойства использует следующий синтаксис.  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
##  <a name="BKMK_GetDirectoryNameOfFileAbove"></a> MSBuild GetDirectoryNameOfFileAbove  
 Функция свойства `GetDirectoryNameOfFileAbove` в MSBuild выполняет поиск файла в каталогах выше текущего каталога в пути.  
  
 Эта функция свойства использует следующий синтаксис.  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 В следующем коде показан пример этого синтаксиса.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
##  <a name="BKMK_GetRegistryValue"></a> MSBuild GetRegistryValue  
 Функция свойства `GetRegistryValue` в MSBuild возвращает значение раздела реестра. Она принимает два аргумента — имя раздела и имя значения — и возвращает значение в реестр. Если не указано имя значения, возвращается значение по умолчанию.  
  
 В следующих примерах показано, как используется эта функция.  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
##  <a name="BKMK_GetRegistryValueFromView"></a> MSBuild GetRegistryValueFromView  
 Функция свойства `GetRegistryValueFromView` в MSBuild получает данные системного реестра с учетом раздела реестра, значения и одного или нескольких упорядоченных представлений реестра. Раздел и значения ищутся в каждом представлении реестра по порядку, пока не будут найдены.  
  
 Синтаксис функции свойства.  
  
 [MSBuild\]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)  
  
 64-разрядная операционная система Windows ведет раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node, содержащий представление реестра HKEY_LOCAL_MACHINE\SOFTWARE для 32-разрядных приложений.  
  
 По умолчанию 32-разрядное приложение, работающее на WOW64, получает доступ к 32-разрядному представлению реестра, а 64-разрядное приложение — к 64-разрядному представлению реестра.  
  
 Доступны следующие представления реестра.  
  
|Представление реестра|Определение|  
|-------------------|----------------|  
|RegistryView.Registry32|Представление реестра для 32-разрядного приложения.|  
|RegistryView.Registry64|Представление реестра для 64-разрядного приложения.|  
|RegistryView.Default|Представление реестра, совпадающее с процессом, на котором работает приложение.|  
  
 Пример.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 Получение данных SLRuntimeInstallPath из раздела ReferenceAssemblies, поиск сначала в 64-разрядном, а затем в 32-разрядном представлении реестра.  
  
##  <a name="BKMK_MakeRelative"></a> MSBuild MakeRelative  
 Функция свойства `MakeRelative` в MSBuild возвращает путь второго пути относительно первого пути. Каждый путь может быть файлом или папкой.  
  
 Эта функция свойства использует следующий синтаксис.  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
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
  
##  <a name="BKMK_ValueOrDefault"></a> MSBuild ValueOrDefault  
 Функция свойства `ValueOrDefault` в MSBuild возвращает первый аргумент, если он не нулевой или пустой. Если первый аргумент нулевой, функция возвращает второй аргумент.  
  
 В следующем примере показано, как используется эта функция.  
  
```  
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
[MSBuild Properties](msbuild-properties1.md)  (Свойства MSBuild)  
[MSBuild Overview](msbuild.md) (Общие сведения о MSBuild)



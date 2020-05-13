---
title: VsCT Компилятор Командно-линейные флаги (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703958"
---
# <a name="vsct-compiler-command-line-flags"></a>Флаги командной строки компилятора VSCT
Компилятор команды Visual Studio (VSCT) обеспечивает коммутаторы командной строки для обеспечения успешной компиляции файлов .vsct.

## <a name="command-line-parameters"></a>Параметры командной строки
 Чтобы просмотреть базовую [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] справку VSCT из окна **команды,** перейдите на путь *установки Visual Studio SDK*(VisualStudioIntegration)Tools-Bin» и введите:

```
vsct /?
```

 Возвращаемые данные:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Символы - (тире) и / (передняя слэш) принимаются к обозначению для указания параметров командной строки.

 Приемлемые флаги и то, что они означают, являются следующими.

|Параметр|Описание|
|------------|-----------------|
|-d|Укажите все дополнительные определенные символы.|
|-I|Укажите дополнительные пути, которые следует использовать при разрешении ссылок файлов.|
|-l|Укажите <xref:System.Globalization.CultureInfo> название культуры, например "en-US".|
|-E|Излучают объекты C в указанном пространстве имен для командных элементов, за которым следуют «C&#124;H&#124;N»:*имя файла,* где C , C, H и заголовок C, N и пространство имен. Пространство имен требуется для C'.|
|-v|Производительность verbose.|

 Переключатель -L поручает компилятору выбрать группу строк для создания двоичного <xref:System.Globalization.CultureInfo> файла .cto, который соответствует заданному названию культуры. Указанное имя культуры должно соответствовать атрибуту Языка одного или нескольких [элементов строк](../../extensibility/strings-element.md) в файле .vsct. Если элемент строкней не имеет атрибута языка, он передается из содержащего [элемент CommandTable.](../../extensibility/commandtable-element.md)

 Файл .vsct может иметь несколько элементов строк, и каждый из них может иметь другой атрибут языка. Глобализация достигается за счет нескольких запусков компилятора VSCT и изменения переключателя -L для каждого имени культуры.

 Если название культуры, данное переключателем -L, не соответствует атрибуту Языка любого элемента Strings, компилятор будет пытаться соответствовать языку, а не региону. Например, если "en-US" не может быть найден, компилятор попытается "en" вместо этого. В противном случае, он будет пытаться текущей культуры операционной системы. В противном случае он будет компилировать первый элемент строки, который он находит.

 Переключатель -E можно использовать для испускаем файла заголовка C-стиля, который содержит символы, используемые командной таблицей, или для испускателя файла C,s, содержащего объекты для символов команд.

 Переключатели -D и -I имеют синтаксис предпроцессорных флагов Cl.exe C с одинаковым названием. -D определения, которые имеют формат X'Y используются для \<расширения XML `Condition` основе определяется> тестов в атрибутах. -Я включаю пути, \<используемые \<для решения \<Включить>, Extern> и Bitmap> файл ссылки. Для получения дополнительной [информации](../../extensibility/vsct-xml-schema-reference.md)см.

 Компилятор VSCT также может декомпилировать ранее построенный двоичный файл. Для этого подавайте бинарный \<файл для> infile.   Если двоичный файл был произведен компилятором VSCT, он будет иметь свои \<символы уже встроенные и будет производить выход с символическими именами в символах> разделе вывода. Если двоичный файл был произведен компилятором CTC, выход будет содержать фактические GUID и идентификаторы. Если файл q.ctsym, который производится текущими версиями Ctc.exe, находится в той же папке, что и файл ввода бинарного файла, символы будут загружены из этого файла и использованы для вывода.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

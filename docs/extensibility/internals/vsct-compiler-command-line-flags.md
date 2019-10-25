---
title: Флаги командной строки компилятора VSCT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722029"
---
# <a name="vsct-compiler-command-line-flags"></a>Флаги командной строки компилятора VSCT
Компилятор Командная таблица Visual Studio (VSCT) предоставляет параметры командной строки для обеспечения успешной компиляции VSCT-файлов.

## <a name="command-line-parameters"></a>Параметры командной строки
 Чтобы просмотреть базовую справку VSCT из **командного** окна [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], перейдите в папку \висуалстудиоинтегратион\тулс\бин\ *путь установки пакета SDK для Visual Studio*и введите:

```
vsct /?
```

 Возвращается следующее:

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
> Символы-(тире) и/(косая черта) являются допустимой нотацией для указания параметров командной строки.

 Ниже приведены допустимые флаги и их значения.

|Параметр|Описание|
|------------|-----------------|
|-D|Укажите любые дополнительные определенные символы.|
|-I|Укажите дополнительные пути включения, которые следует использовать при разрешении ссылок на файлы.|
|-L|Укажите имя языка и региональных параметров <xref:System.Globalization.CultureInfo>, например "en-US".|
|-E|Выдавать C# объекты в указанном пространстве имен для командных элементов, за&#124;которыми&#124;следует [CH N]: C#filename, где C++ C =, H = Header, N = Namespace. Пространство имен является обязательным для C#.|
|-v|Подробный вывод.|

 Параметр-L указывает компилятору выбрать группу строк для создания файла binary. CTO, соответствующего заданному имени языка и региональных параметров <xref:System.Globalization.CultureInfo>. Указанное имя языка и региональных параметров должно соответствовать атрибуту Language одного или нескольких [элементов strings](../../extensibility/strings-element.md) в vsct файле. Если у элемента строк нет атрибута языка, он наследуется от содержащего его [элемента коммандтабле](../../extensibility/commandtable-element.md).

 Файл. vsct может содержать несколько строковых элементов, и у каждого из них может быть другой атрибут языка. Глобализация достигается за счет многократного запуска компилятора VSCT и изменения параметра-L для каждого имени языка и региональных параметров.

 Если имя языка и региональных параметров, заданное параметром-L, не соответствует атрибуту Language любого элемента Strings, компилятор будет пытаться сопоставить язык, а не регион. Например, если не удается найти "en-US", компилятор попытается использовать "en". В этом случае будет выполнена попытка использовать текущий язык и региональные параметры операционной системы. Это приведет к компиляции первого найденного элемента Strings.

 Параметр-E можно использовать для создания заголовочного файла в стиле C, содержащего символы, используемые в командной таблице, или для выдачи C# файла, содержащего объекты для символов команды.

 Переключатели-D и-I имеют синтаксис для флагов препроцессора в CL. exe C с одинаковыми именами. -D определений, имеющие формат X = Y, используются для расширения \<Defined на основе XML > тесты в атрибутах `Condition`. -I включает пути для разрешения \<Include >, \<Extern > и \<Bitmap > ссылок на файлы. Дополнительные сведения см. в [справочнике по XML-схеме VSCT](../../extensibility/vsct-xml-schema-reference.md).

 Компилятор VSCT также может декомпилировать ранее созданный двоичный файл. Для этого укажите двоичный файл для > \<infile.   Если двоичный файл был создан компилятором VSCT, его символы уже внедрены и будут выдавать выходные данные с символьными именами в \<Symbols > разделе выходных данных. Если двоичный файл был создан компилятором CTC, выходные данные будут содержать фактические идентификаторы GUID и идентификаторы. Если файл *. ctsym, созданный текущими версиями CTC. exe, находится в той же папке, что и входной двоичный файл, то символы будут загружены из этого файла и использованы для вывода.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
---
title: "Флаги командной строки компилятора VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-файлы, компиляция"
  - "Компиляция файла таблицы команд (VSCT-файлы)"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Флаги командной строки компилятора VSCT
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Компилятор Visual Studio команды таблицы (VSCT) предоставляет параметры командной строки для обеспечения успешной компиляции vsct-файлы.  
  
## <a name="command-line-parameters"></a>Параметры командной строки  
 Для просмотра основных VSCT из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **команда** окно, перейдите к *путь установки Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ папку и введите:  
  
```  
vsct /?  
```  
  
 Возвращает:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Символы - (дефис) и / (косая черта) являются оба принятые нотации, указывающий параметры командной строки.  
  
 Ниже перечислены допустимые флаги и они означают.  
  
|Параметр|Описание|  
|------------|-----------------|  
|-D|Укажите любые дополнительные определенных символов.|  
|-I|Указать, что дополнительные пути поиска включаемых файлов, следует использовать при разрешении ссылок на файлы.|  
|-L|Укажите <xref:System.Globalization.CultureInfo> имя языка и региональных параметров, например «en US».|  
|-E|Возвращает объектов C# в указанном пространстве имен для элементов, команда, следуют [C &#124; С &#124; N]:*filename*где C = C#, H = заголовка C++, N = пространство имен. Пространство имен является обязательным для C#.|  
|-v|Подробный вывод.|  
  
 Переключатель -L указывает компилятору на необходимость выбрать группу строк для получения .cto двоичный файл, соответствующий данной <xref:System.Globalization.CultureInfo> имя языка и региональных параметров. Имя заданного языка и региональных параметров должно соответствовать атрибуту языка из одного или нескольких [элемент строки](../../extensibility/strings-element.md) в файле .vsct. Если элемент строки не имеет языка атрибутов, оно наследуется от содержащего [элемент CommandTable](../../extensibility/commandtable-element.md).  
  
 Файла .vsct может иметь несколько элементов строки, и каждый может иметь другой атрибут языка. Глобализация достигается путем запуска компилятора VSCT несколько раз и изменив переключатель -L для каждого имени языка и региональных параметров.  
  
 Если имя языка и региональных параметров, заданное параметром -L соответствует атрибут Language любого элемента строки, компилятор будет пытаться найти совпадения язык и регион не. Например если не удается найти «en US», компилятор попытается вместо «en». Он попытается текущую культуру операционной системы. После неудачной компиляции первый элемент строки, найденные.  
  
 Можно использовать параметр -E для порождения файл заголовка C-стиль, содержащий символы, используемые в таблице команд или для создания файла C#, содержащий объекты для управляющие символы.  
  
 -D и -коммутаторы иметь синтаксис флагов препроцессора Cl.exe C, которые имеют одинаковые имена. – D расширения на основе XML используются определения X = Y в формате \< определенные> тесты в `Condition` атрибуты. — Включать пути используются для разрешения \< Include>, \< Extern> и \< точечный рисунок> ссылки на файлы. Дополнительные сведения см. в разделе [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Компилятор VSCT также может декомпилировать ранее построенный двоичный файл. Чтобы сделать это, укажите двоичный файл для \< infile>.   Если двоичный файл был создан с помощью компилятора VSCT, он уже внедренных символов, а вывод с символические имена в \< символы> части выходных данных. Если двоичный файл был создан с помощью компилятора CTC, выход будет содержать фактическое GUID и идентификаторы. Если *.ctsym файл, созданный текущей версии Ctc.exe находится в той же папке двоичный файл ввода, символы будут загружаться из этого файла и используется для вывода.  
  
## <a name="see-also"></a>См. также  
 [Таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
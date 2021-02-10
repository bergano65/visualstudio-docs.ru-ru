---
title: Использование выражений в отладчике | Документация Майкрософт
description: Сведения о том, какие выражения языка не поддерживаются средствами оценки выражений в отладчике Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc17892697e16c24e3bb1fae5aa956123ee4e7bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870796"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Выражения в отладчике Visual Studio
В состав отладчика Visual Studio входят вычислители выражений, которые работают при вводе выражения в диалоговое окно **Быстрая проверка** , окно **Контрольные значения** или окно **Интерпретация** . Вычислители выражений также работают в окне **точки останова** и многих других местах в отладчике.

В следующих разделах описываются ограничения на вычисление выражений для языков, поддерживаемых Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Выражения F# не поддерживаются.
Выражения F# не распознаются. При отладке кода F# необходимо перевести выражения в синтаксис C# перед вводом этих выражений в окно отладчика или диалоговое окно. Выполняя перевод выражений F# в синтаксис C#, помните, что в C# в качестве оператора проверки равенства используется `==` , а в F# — одинарный знак `=`.

## <a name="c-expressions"></a>Выражения C++
Информацию об использовании операторов контекста с выражениями в C++ см. в разделе [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Неподдерживаемые выражения в C++

#### <a name="constructors-destructors-and-conversions"></a>Конструкторы, деструкторы и преобразования
Вы не можете вызвать конструктор или деструктор объекта явно или неявно. Например, следующее выражение вызывает конструктор явным способом, что приводит к сообщению об ошибке:

```C++
my_date( 2, 3, 1985 )
```

Функция преобразования не может быть вызвана, если результатом преобразования является класс. Такое преобразование включает создание объекта. Например, если `myFraction` — экземпляр класса `CFraction`, в котором определен оператор функции преобразования `FixedPoint`, то следующее выражение вызовет ошибку:

```C++
(FixedPoint)myFraction
```

Вы не можете вызывать операторы new и delete. Например, следующее выражение не поддерживается:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Макросы препроцессора
Макросы препроцессора не поддерживаются в отладчике. Например, если константа `VALUE` объявлена как `#define VALUE 3`, нельзя использовать `VALUE` в окне **Контрольные значения** . Чтобы обойти это ограничение, заменяйте `#define`перечислениями и функциями, где это возможно.

### <a name="using-namespace-declarations"></a>Объявления пространства имен using
Объявления `using namespace` использовать нельзя.  Чтобы обратиться к имени типа или переменной вне текущего пространства имен, необходимо использовать полное имя.

### <a name="anonymous-namespaces"></a>Анонимные пространства имен
Анонимные пространства имен не поддерживаются. Если имеется следующий код, нельзя добавить `test` в окно контрольных значений:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Использование встроенных функций отладчика для сохранения состояния
С помощью встроенных функций отладчика можно вызывать некоторые функции C/C++ в выражениях, не изменяя при этом состояние приложения.

Встроенные функции отладчика:

- Гарантированно безопасны: выполнение встроенной функции отладчика не приведет к повреждению отлаживаемого процесса.

- Могут использоваться в любых выражениях, в том числе в сценариях, не допускающих побочные эффекты и вычисление функций.

- Работают в сценариях, в которых обычные вызовы функций невозможны, как, например, при отладке минидампа.

  Кроме того, встроенные функции отладчика могут сделать вычисление выражений более удобным. Например, в качестве условия останова намного удобнее использовать выражение вида `strncmp(str, "asd")` , чем выражение `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Область|Встроенные функции|
|----------|-------------------------|
|**Длина строки**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Сравнение строк**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Поиск строки**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](/previous-versions/bb432242(v=vs.85)), [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Для этих функций требуется, чтобы отлаживаемый процесс выполнялся в Windows 8. Для отладки файлов дампа, сгенерированных устройством Windows 8, также необходимо, чтобы компьютер Visual Studio работал под управлением Windows 8. В то же время, если устройство Windows 8 отлаживается удаленно, допускается работа компьютера Visual Studio под управлением Windows 7.|
|**Прочее**|__log2 // Возвращает значение логарифма по основанию 2 от указанного целого числа, округленное до ближайшего меньшего целого числа.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] и operator(index<>)<br /><br />ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)<br /><br />ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] и operator(tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] и operator(index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] и operator(tiled_index<>)<br /><br />TreeTraverse_Init // Инициализирует новое прохождение по дереву<br /><br />TreeTraverse_Next // Возвращает узлы в дереве<br /><br />TreeTraverse_Skip // Пропускает узлы при незавершенном прохождении по дереву|

## <a name="ccli---unsupported-expressions"></a>Неподдерживаемые выражения C++/CLI

- Приведения с использованием указателей и определенные пользователем приведения не поддерживаются.

- Сравнение и назначение объектов не поддерживается.

- Перегруженные операторы и перегруженные функции не поддерживаются.

- Упаковка-преобразование и распаковка-преобразование не поддерживаются.

- Оператор`Sizeof` не поддерживается.

## <a name="c---unsupported-expressions"></a>Неподдерживаемые выражения C#

### <a name="dynamic-objects"></a>Динамические объекты
В выражениях отладчика можно использовать статически типизированные переменные как динамические. При вычислении в окне контрольных значений объектов, реализующих интерфейс <xref:System.Dynamic.IDynamicMetaObjectProvider>, добавляется узел динамического представления. Узел динамического представления отображает члены объектов, но не позволяет изменять значения этих членов.

Следующие возможности динамических объектов не поддерживаются:

- составные операторы `+=`, `-=`, `%=`, `/=`и `*=`;

- многие приведения, включая приведения числовых типов и приведения аргументов типа;

- вызовы методов с более чем двумя аргументами;

- методы получения свойств с более чем двумя аргументами;

- методы задания свойств с аргументами;

- присвоение индексатору;

- логические операторы `&&` и `||`.

### <a name="anonymous-methods"></a>Анонимные методы
Создание анонимных методов не поддерживается.

## <a name="visual-basic---unsupported-expressions"></a>Неподдерживаемые выражения Visual Basic

### <a name="dynamic-objects"></a>Динамические объекты
В выражениях отладчика можно использовать статически типизированные переменные как динамические. При вычислении в окне "Контрольные значения" объектов, реализующих интерфейс <xref:System.Dynamic.IDynamicMetaObjectProvider>, добавляется узел динамического представления. Узел динамического представления отображает члены объектов, но не позволяет изменять значения этих членов.

Следующие возможности динамических объектов не поддерживаются:

- составные операторы `+=`, `-=`, `%=`, `/=`и `*=`;

- многие приведения, включая приведения числовых типов и приведения аргументов типа;

- вызовы методов с более чем двумя аргументами;

- методы получения свойств с более чем двумя аргументами;

- методы задания свойств с аргументами;

- присвоение индексатору;

- логические операторы `&&` и `||`.

### <a name="local-constants"></a>Локальные константы
Локальные константы не поддерживаются.

### <a name="import-aliases"></a>Импорт псевдонимов
Импорт псевдонимов не поддерживается.

### <a name="variable-declarations"></a>Объявления переменных
В окнах отладчика не поддерживается явное объявление новых переменных. Однако можно присвоить значение новой неявной переменной в окне **Интерпретация** . Эти неявные переменные инкапсулированы в сеансе отладки и недоступны вне отладчика. Например, оператор `o = 5` неявно создает переменную `o` и присваивает ей значение 5. Если отладчику не удается определить тип для таких неявных переменных, они имеют тип **Object** .

### <a name="unsupported-keywords"></a>Неподдерживаемые ключевые слова

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Ключевые слова пространства имен или уровня модуля, например `End Sub` или `Module`.

## <a name="see-also"></a>См. также
- [Определители формата в C++](../debugger/format-specifiers-in-cpp.md)
- [Оператор Context (C++)](../debugger/context-operator-cpp.md)
- [Определители формата в C#](../debugger/format-specifiers-in-csharp.md)
- [Псевдопеременные](../debugger/pseudovariables.md)
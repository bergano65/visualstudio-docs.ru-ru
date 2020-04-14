---
title: Создание пользовательских представлений для объектов C++
description: Используйте фреймворк Natvis, чтобы настроить способ отображения Visual Studio в отладчике
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224515"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Создание пользовательских представлений объектов C-в отладчике с помощью платформы Natvis

Инфраструктура Visual Studio *Natvis* настраивает способ появления типов native в переменных окнах отладчика, таких как окна **Locals** и **Watch,** а также в **DataTips.** Визуализации Natvis могут помочь сделать создаваемые типы более заметными во время отладки.

Natvis заменяет файл *autoexp.dat* в более ранних версиях Visual Studio с помощью синтаксиса XML, улучшенной диагностики, версии и многократной поддержки файлов.

> [!NOTE]
> Настройки Natvis работают с классами и структурами, но не набирают.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Визуализации Natvis

Для создания правил визуализации для создаваемых типов используется платформа Natvis, чтобы разработчикам было легче видеть их во время отладки.

Например, на следующей иллюстрации показана переменная типа [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) в окне отладчика без применения пользовательских визуализаций.

![Визуализация элемента TextBox по умолчанию](../debugger/media/dbg_natvis_textbox_default.png "Визуализация элемента TextBox по умолчанию")

В выделенной строке показано свойство `Text` класса `TextBox` . Сложная иерархия классов затрудняет поиск этого свойства. Отладчик не знает, как интерпретировать пользовательский тип строки, поэтому вы не можете видеть строку, удерживаемую внутри текстового ящика.

То `TextBox` же самое выглядит гораздо проще в переменном окне, когда применяются пользовательские правила визуализатора Natvis. Важные участники класса отображаются вместе, а отладчик показывает базовое значение строки пользовательского типа строки.

![Данные TextBox с использованием визуализатора](../debugger/media/dbg_natvis_textbox_visualizer.png "Данные TextBox с использованием визуализатора")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Использование файлов .natvis в проектах СЗЗ

Natvis использует файлы *.natvis* для указания правил визуализации. Файл *.natvis* — это файл XML с расширением *.natvis.* Схема Natvis определена в *%VSINSTALLDIR%*

Основная структура файла *.natvis* — `Type` это один или несколько элементов, представляющих записи визуализации. Полностью квалифицированное `Type` название каждого `Name` элемента указывается в его атрибуте.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio предоставляет некоторые файлы *.natvis* в *файле %VSINSTALLDIR%-Common7-Пакеты-Debugger-Visualizers.* Эти файлы имеют правила визуализации для многих распространенных типов и могут служить примерами для написания визуализаций для новых типов.

### <a name="add-a-natvis-file-to-a-c-project"></a>Добавление файла .natvis в проект «СЗ»

Вы можете добавить файл *.natvis* в любой проект СЗЗ.

**Чтобы добавить новый файл *.natvis:***

1. Выберите узлы проекта «СЗ» в **Solution Explorer**и выберите**новый элемент** **Project** > Add или нажмите на проект вправо и выберите **Добавить** > **новый элемент.**

1. В диалоге **Добавить новый элемент** выберите файл визуализации**визуализации visual** >  **C'S** > Utility**Debugger (.natvis).**

1. Назовите файл и **выберите Добавить**.

   Новый файл добавляется в **Solution Explorer**и открывается в панели документов Visual Studio.

Отладка Visual Studio загружает файлы *.natvis* в проекты СЗ и по умолчанию также включает их в файл *.pdb* при сборке проекта. Если отладить построенное приложение, отладчик загружает файл *.natvis* из файла *.pdb,* даже если проект не открыт. Если вы не хотите, чтобы файл *.natvis* был включен в *.pdb,* вы можете исключить его из построенного файла *.pdb.*

**Чтобы исключить файл *.natvis* из *.pdb:***

1. Выберите файл *.natvis* в **Solution Explorer**и выберите значок **Свойства** или нажмите на файл вправо и выберите **Свойства.**

1. Падение вниз стрелка рядом с **исключены из сборки** и выберите **Да**, а затем выберите **OK**.

>[!NOTE]
>Для отладки исполняемых проектов используйте элементы решения для добавления любых файлов *.natvis,* которые не входят в *.pdb,* так как нет проекта КЗ.

>[!NOTE]
>Правила Natvis, загруженные из *.pdb,* применяются только к типам модулей, на которые ссылается *.pdb.* Например, если *Module1.pdb* имеет запись Natvis `Test`для типа имени, `Test` он применяется только к классу в *Module1.dll*. Если другой модуль также определяет `Test`класс с именем, запись *Module1.pdb* Natvis не распространяется на него.

**Для установки и регистрации файла *.natvis* через пакет VSIX:**

Пакет VSIX может устанавливать и регистрировать файлы *.natvis.* Независимо от того, где они установлены, все зарегистрированные файлы *.natvis* автоматически подбираются во время отладки.

1. Включите файл *.natvis* в пакет VSIX. Например, для следующего файла проекта:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Зарегистрируйте файл *.natvis* в файле *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Местоположение файлов Natvis

Вы можете добавить файлы *.natvis* в каталог пользователя или в системный каталог, если вы хотите, чтобы они применялись к нескольким проектам.

Файлы *.natvis* оцениваются в следующем порядке:

1. Любые файлы *.natvis,* встроенные в *.pdb,* которые вы отлажаете, за исключением случаев, когда в загруженном проекте нет файла с тем же именем.

2. Любые файлы *.natvis,* которые находятся в загруженном проекте C или на высшем уровне решения. Эта группа включает в себя все загруженные проекты КЗ, включая библиотеки классов, но не проекты на других языках.

3. Любые файлы *.natvis* установлены и зарегистрированы через пакет VSIX.

::: moniker range="vs-2017"

4. Каталог Natvis, специфичный для пользователей (например, *%USERPROFILE% -Документы/Визуальная студия 2017 г.).*

::: moniker-end

::: moniker range=">= vs-2019"

4. Каталог Natvis, специфичный для пользователей (например, *%USERPROFILE% -Документы/Визуальная студия 2019 г.).*

::: moniker-end

5. Каталог Natvis всей системы (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Этот каталог имеет файлы *.natvis,* которые установлены с Visual Studio. Если у вас есть разрешения администратора, можно добавить файлы в этот каталог.

## <a name="modify-natvis-files-while-debugging"></a>Изменение файлов .natvis во время отладки

Можно изменить файл *.natvis* в IDE во время отладки его проекта. Откройте файл в том же экземпляре Visual Studio, с помощью которых вы отладочнетесь, измените его и сохраните. Как только файл сохраняется, окна **Watch** and **Locals** обновляются, чтобы отразить изменения.

Вы также можете добавить или удалить файлы *.natvis* в решении, которое вы отлажавить, и Visual Studio добавляет или удаляет соответствующие визуализации.

Вы не можете обновлять файлы *.natvis,* встроенные в файлы *.pdb* во время отладки.

Если вы измените файл *.natvis* за пределами Visual Studio, изменения не вступают в силу автоматически. Для обновления окон отладчика можно пересмотреть команду **.natvisreload** в окне **Немедленного.** Затем изменения вступают в силу без перезапуска сеанса отладки.

Также используйте команду **.natvisreload** для обновления файла *.natvis* до более новой версии. Например, файл *.natvis* может быть проверен в исходном элементе управления, и вы хотите получить последние изменения, внесенные кем-то другим.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Выражения и форматирование
Визуализации Natvis используют выражения C++ для указания элементов данных для отображения. В дополнение к усовершенствованиям и ограничениям выражений C'в отладчике, которые описаны в [операторе контекста (КЗ),](../debugger/context-operator-cpp.md)следует знать следующее:

- Выражения Natvis вычисляются в контексте визуализируемого объекта, а не текущего кадра стека. Например, `x` в выражении Natvis относится поле, названное **x** в визуализанном объекте, а не к локальной переменной, названной **x** в текущей функции. Вы не можете получить доступ к локальным переменным в выражениях Natvis, хотя вы можете получить доступ к глобальным переменным.

- Выражения Natvis не позволяют оценивать функции или побочные эффекты. Операторы функциональных вызовов и операторов назначения игнорируются. Поскольку [встроенные функции отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) не зависимы от побочных эффектов, их можно свободно вызывать из любого выражения Natvis, даже если другие вызовы функций запрещены.

- Чтобы контролировать отображение выражения, можно использовать любой из спецификаций формата, описанных в [спецификациях формата в СЗ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Спецификаторы формата игнорируются, когда запись используется внутри Natvis, `Size` например, выражение в [расширении ArrayItems.](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)

## <a name="natvis-views"></a>Представления Natvis

Можно определить различные представления Natvis для отображения типов по-разному. Например, вот `std::vector` визуализация, которая определяет упрощенное представление под названием `simple`. `DisplayString` Элементы `ArrayItems` и элементы отображаемые в представлении по умолчанию и представлении, `simple` в то время как `[size]` `[capacity]` элементы не отображаемы в представлении. `simple`

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

В окне **Watch** используйте спецификацию формата **просмотра,** чтобы указать альтернативное представление. Простое представление отображается как **vec,view(просто)**:

![Окно контрольных значений с простым представлением](../debugger/media/watch-simpleview.png "Окно контрольных значений с простым представлением")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Ошибки Натвиса

Когда отладчик сталкивается с ошибками в вводе визуализации, он игнорирует их. Он либо отображает тип в своей сырой форме, либо выбирает другую подходящую визуализацию. Вы можете использовать диагностику Natvis, чтобы понять, почему отладчик проигнорировал запись визуализации, а также увидеть основные ошибки синтаксиса и разбора.

**Чтобы включить диагностику Natvis:**

- Под **параметры инструментов** > **Options** (или**Параметры** **отъебать)** > > **отладки** > **выходного окна**, установите диагностические сообщения **Natvis (только с КЗ)** на **ошибку,** **Предупреждение**, или **Verbose**, а затем выберите **OK.**

Ошибки отображаются в окне **вывода.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Справочник по синтаксису Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Элемент AutoVisualizer
Элемент `AutoVisualizer` — это корневой узел *NATVIS*-файла, который содержит атрибут `xmlns:` пространства имен.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Элемент `AutoVisualizer` может иметь [тип,](#BKMK_Type) [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), и [CustomVisualizer](#BKMK_CustomVisualizer) детей.

### <a name="type-element"></a><a name="BKMK_Type"></a>Элемент типа

Основной `Type` выглядит как этот пример:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Элемент `Type` определяет:

1. Для какого типа визуализация должна `Name` использоваться (атрибут).

2. Как должно выглядеть значение объекта этого типа (элемент `DisplayString` ).

3. Как должны выглядеть участники типа, когда пользователь расширяет тип в `Expand` переменном окне (узла).

#### <a name="templated-classes"></a>Шаблонные классы
Атрибут `Name` `Type` элемента принимает звездочку `*` как символ подстановочного знака, который может быть использован для шаблонных имен классов.

В следующем примере используется та же визуализация, `CAtlArray<int>` является `CAtlArray<float>`ли объект. Если есть специфическая запись визуализации `CAtlArray<float>`для, то она имеет приоритет над общим.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Можно ссылаться на параметры шаблона в записи визуализации с помощью макросов $T1, $T2 и так далее. Чтобы найти примеры этих макросов, см. *NATVIS*-файлы, поставляемые в комплекте с Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Сопоставление типов визуализатора
Если запись визуализации не проверяется, используется следующая доступная визуализация.

#### <a name="inheritable-attribute"></a>Атрибут Inheritable
Дополнительный `Inheritable` атрибут определяет, применяется ли визуализация только к базовому типу, или к базовому типу и всем полученным типам. Значение `Inheritable` по умолчанию — `true`.

В следующем примере визуализация применяется `BaseClass` только к типу:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Атрибут Priority

Дополнительный `Priority` атрибут определяет порядок использования альтернативных определений, если определение не может разобрать. Возможные значения `Priority` являются: `Low` `MediumLow`,`Medium` `MediumHigh`, `High`, и . Значение по умолчанию — `Medium`. Атрибут `Priority` отличается только между приоритетами в одном файле *.natvis.*

Следующий пример сначала разбирает запись, которая соответствует 2015 STL. Если это не разобрать, он использует альтернативную запись для версии 2013 STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Атрибут Optional
Вы можете `Optional` поместить атрибут на любой узла. Если субэкспрессия внутри факультативного узла не разбор, отладчик игнорирует этот уденец, но применяет остальные `Type` правила. В следующем типе `[State]` является обязательным, а `[Exception]` — необязательным.  Если `MyNamespace::MyClass` у нас`M_exceptionHolder`есть поле `[State]` под названием q, оба узла `[Exception]` `_M_exceptionHolder` и узла `[State]` отображаются, но если нет поля, появляется только узла.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Атрибут Condition

Дополнительный `Condition` атрибут доступен для многих элементов визуализации и определяет, когда использовать правило визуализации. Если выражение внутри атрибута состояния `false`устраняется, правило визуализации не применяется. Если он оценивает, `true`или нет `Condition` атрибута, визуализация применяется. Этот атрибут можно использовать для логики if-else в записях визуализации.

Например, следующая визуализация `DisplayString` имеет два элемента для типа смарт-указателя. Когда `_Myptr` элемент пуст, состояние первого `DisplayString` элемента `true`решается на, так что форма отображает. Когда `_Myptr` элемент не пуст, условие оценивается как, `DisplayString` и второй элемент отображается. `false`

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Атрибут IncludeView и ExcludeView

`IncludeView` Атрибуты `ExcludeView` и атрибуты указывают элементы для отображения или неотображения в определенных представлениях. Например, `std::vector`в следующей спецификации `simple` Natvis представления не `[size]` `[capacity]` отображается и элементы.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Вы можете `IncludeView` использовать `ExcludeView` и атрибуты на типах и на отдельных членах.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Элемент версии
Элемент `Version` прицелирует запись визуализации к определенному модулю и версии. Элемент `Version` помогает избежать столкновений имен, уменьшает непреднамеренные несоответствия и позволяет различные визуализации для различных версий типов.

Если общий файл заголовка, используемый различными модулями, определяет тип, визуализация версии появляется только тогда, когда тип находится в указанной версии модуля.

В следующем примере визуализация применима `DirectUI::Border` только к `Windows.UI.Xaml.dll` типу, найденного в версии 1.0 до 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Вам не нужно `Min` и `Max`. Они являются необязательными атрибутами. Символы подстановочных знаков не поддерживаются.

Атрибут `Name` находится в формате *filename.ext,* например, *hello.exe* или *some.dll*. Имена путей не допускаются.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Элемент DisplayString
Элемент `DisplayString` определяет строку для отображаемого как значение переменной. Принимает произвольные строки в сочетании с выражениями. Весь код внутри фигурных скобок интерпретируется как выражение. Например, следующая `DisplayString` запись:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Означает, что переменные типа `CPoint` дисплея, как на этой иллюстрации:

 ![Использование элемента DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Использование элемента DisplayString")

В `DisplayString` `x` выражении, `y`и , `CPoint`которые являются членами , находятся внутри фигурные скобки, так что их значения оцениваются. Пример также показывает, как вы можете избежать фигурные скобки `{{` `}}` с помощью двойных фигурных скобки ( или ).

> [!NOTE]
> Элемент `DisplayString` является единственным элементом, который принимает произвольные строки и синтаксис фигурных скобок. Все остальные элементы визуализации принимают только выражения, которые может оценить отладчик.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Элемент StringView

Элемент `StringView` определяет значение, которое отладчик может отправить ввстроенный текстовый визуализатор. Например, с учетом следующей `ATL::CStringT` визуализации для типа:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Объект `CStringT` отображается в переменном окне, как этот пример:

![Элемент CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Элемент CStringT DisplayString")

Добавление `StringView` элемента говорит отладчику, что он может отображать значение как визуализацию текста.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Во время отладки можно выбрать значок увеличительного стекла рядом с переменной, а затем выбрать **text Visualizer** для отображения строки, на которую **m_pszData** указывает.

 ![Данные CStringT с визуализатором StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Данные CStringT с визуализатором StringView")

Выражение `{m_pszData,su}` включает в себя specifier формата СЗ **su,** для отображения значения в виде строки Unicode. Для получения дополнительной [информации см.](../debugger/format-specifiers-in-cpp.md)

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Расширить элемент

Дополнительный `Expand` узло настраивает дочерние элементов визуализированного типа при расширении типа в переменном окне. Узла `Expand` принимает список детских узлов, определяющих элементы ребенка.

- Если `Expand` узла не указано в записи визуализации, дети используют правила расширения по умолчанию.

- Если `Expand` узла не указано, под ним нет детских узлов, тип не расширяется в окнах отладчика.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Расширение элемента

 Элемент `Item` является самым основным и общим `Expand` элементом в узлах. `Item` определяет один дочерний элемент. Например, `CRect` класс с `top` `left` `right`полями, `bottom` и имеет следующую запись визуализации:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

В окне отладчика `CRect` тип выглядит следующим образом:

![CRect с расширением элемента Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect с расширением элемента Item")

Отладчик оценивает выражения, указанные `Width` в `Height` элементах, и показывает значения в столбце **значения** переменного окна.

Отладчик автоматически создает узла **«Raw View»** для каждого пользовательского расширения. На предыдущем скриншоте отображается расширенный узла **«Raw View»,** чтобы показать, как необработанный вид объекта по умолчанию отличается от визуализации Natvis. Расширение по умолчанию создает поддерево для базового класса и перечисляет все члены данных базового класса как дети.

> [!NOTE]
> Если выражение элемента указывает на сложный тип, то сам узла **Элемента** расширяется.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Используйте узел `ArrayItems` , чтобы отладчик Visual Studio интерпретировал тип как массив и отображал его отдельные элементы. Хорошим примером является визуализация для `std::vector` :

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` указывает его отдельные элементы, когда он развернут в окне переменных:

![std::vector с использованием расширения ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector с использованием расширения ArrayItems")

Узла `ArrayItems` должно быть:

- Выражение `Size` (которое должно вычисляться с получением целого числа) для отладчика, чтобы понять длину массива.
- Выражение, `ValuePointer` указывавшее на первый элемент (который должен `void*`быть указателем типа элемента, который не является).

Значение по умолчанию нижней границы массива — 0. Чтобы переопределить значение, `LowerBound` используйте элемент. В файлах *.natvis,* поставляемых visual Studio, есть примеры.

>[!NOTE]
>Вы можете `[]` использовать оператора, `vector[i]`например, с любой одномерной визуализации массива, который использует, `ArrayItems`даже если сам тип (например) `CATLArray`не позволяет этому оператору.

Можно также указать многомерные массивы. В этом случае отладчику требуется немного больше информации для правильного отображения элементов ребенка:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`определяет, находится ли массив в ряд-основном или столбцово-основном порядке.
- `Rank` указывает ранг массива.
- Элемент `Size` принимает неявный параметр `$i`, вместо которого подставляет индекс измерения для нахождения длины массива в этом измерении. В предыдущем примере `_M_extent.M_base[0]` выражение должно дать длину 0-го измерения, `_M_extent._M_base[1]` 1-го и так далее.

Вот как двухмерный `Concurrency::array` объект выглядит в окне отладчика:

![Двухмерный массив с расширением ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Двухмерный массив с расширением ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Расширение IndexListItems

Расширение можно `ArrayItems` использовать только в том случае, если элементы массива расположены в памяти. Отладчик попадает в следующий элемент, просто приравня указатель. Если вам нужно манипулировать индексом к узлам значения, используйте `IndexListItems` узлы. Вот визуализация с узлами: `IndexListItems`

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

Единственное различие `ArrayItems` `IndexListItems` между `ValueNode`и является , который ожидает полного выражения `$i` i<sup>элемент</sup> с неявным параметром.

>[!NOTE]
>Вы можете `[]` использовать оператора, `vector[i]`например, с любой одномерной визуализации массива, который использует, `IndexListItems`даже если сам тип (например) `CATLArray`не позволяет этому оператору.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Расширение LinkedListItems

Если визуализированный тип представляет связанный список, отладчик может отображать его дочерние элементы с помощью узла `LinkedListItems` . Следующая визуализация `CAtlList` для `LinkedListItems`типа использует:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

Элемент `Size` ссылается на длину списка. `HeadPointer` указывает на первый элемент, `NextPointer` ссылается на следующий элемент, а `ValueNode` ссылается на значение элемента.

Отладчик оценивает `NextPointer` и `ValueNode` выражения в контексте `LinkedListItems` элемента узла, а не типа родительского списка. В предыдущем примере `CAtlList` `CNode` есть класс `atlcoll.h`(найденный в), который является узлом связанного списка. `m_pNext`и `m_element` являются полями этого `CNode` класса, а не `CAtlList` класса.

`ValueNode`может быть оставлен пустым `this` или использовать `LinkedListItems` для обозначения самого узла.

#### <a name="customlistitems-expansion"></a>Расширение LinkedListItems

Расширение `CustomListItems` позволяет записывать настраиваемую логику для обхода структуры данных, например хэш-таблицы. `CustomListItems` Используйте для визуализации структур данных, которые могут использовать выражения СЗ для всего, что `ArrayItems` `IndexListItems`вам `LinkedListItems`нужно оценить, но не совсем соответствуют плесени для , или .

Можно использовать `Exec` для выполнения кода `CustomListItems` внутри расширения, используя переменные и объекты, определенные в расширении. Вы можете использовать логических операторов, арифметических операторов и операторов назначения с `Exec`. Вы не можете `Exec` использовать для оценки функций, за исключением функций внутренней [отладки,](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) поддерживаемых оценщиком экспрессии СЗ.

Следующий визуализатор `CAtlMap` для `CustomListItems` является прекрасным примером, где это уместно.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Расширение TreeItems
 Если визуализированный тип представляет дерево, отладчик может пройти дерево отображать его дочерние элементы с помощью узла `TreeItems` . Вот визуализация для `std::map` типа с `TreeItems` помощью узла:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Синтаксис похож на `LinkedListItems` узла. `LeftPointer`, `RightPointer`и `ValueNode` оцениваются в контексте класса узлов дерева. `ValueNode`может быть оставлен `this` пустым или `TreeItems` использовать для обозначения самого узла.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Расширение ExpandedItem
 Элемент `ExpandedItem` генерирует агрегированное представление ребенка, отображая свойства базовых классов или членов данных, как если бы они были детьми визуализированного типа. Отладчик оценивает указанное выражение и прилагает детские узлы результата к списку детей визуализированного типа.

Например, тип `auto_ptr<vector<int>>` «умная указка» обычно отображается как:

 ![автоматический&#95;ptr&#60;вектор&#60;Int&#62;&#62; расширение по умолчанию](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Расширение по умолчанию")

 Чтобы увидеть значения вектора, необходимо просверлить два уровня в `_Myptr` переменном окне, проходя через член. При добавлении элемента `ExpandedItem` можно исключить переменную `_Myptr` из иерархии и просмотреть непосредственно элементы вектора elements:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![авто&#95;ptr&#60;вектор&#60;Int&#62;&#62; ExpandedItem расширения](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Расширение ExpandedItem")

В следующем примере показано, как агрегировать свойства из базового класса в производном классе. Предположим, класс `CPanel` является производным от `CFrameworkElement`. Вместо повторения свойств, которые приходят `CFrameworkElement` из базового класса, визуализация `ExpandedItem` узлов прилагает `CPanel` эти свойства к списку детей класса.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Здесь необходим спецификатор формата **nd**, который отключает сопоставление визуализации для производного класса. В противном `*(CFrameworkElement*)this` случае `CPanel` выражение может привести к повторному применению визуализации, поскольку правила сопоставления типа визуализации по умолчанию считают его наиболее подходящим. Используйте спецификацию **формата nd,** чтобы поручить отладчику использовать визуализацию базового класса или расширение по умолчанию, если базовый класс не имеет визуализации.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Расширение синтетического элемента
 Там, где элемент `ExpandedItem` предоставляет более плоское представление данных, устраняя иерархии, узел `Synthetic` делает обратное. Это позволяет создать искусственный элемент ребенка, который не является результатом выражения. Искусственный элемент может иметь свои собственные элементы ребенка. В следующем примере визуализация для типа `Concurrency::array` использует узел `Synthetic` , чтобы показать диагностическое сообщение пользователю.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Параллель:Array с расширением синтетического элемента](../debugger/media/dbg_natvis_expand_synthetic.png "Параллель:Array с расширением синтетического элемента")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Элемент HResult
 Элемент `HResult` позволяет настроить информацию, отображаемую для **HRESULT** в окнах отладчика. Элемент `HRValue` должен содержать 32-разрядное значение **HRESULT**, который требуется настроить. Элемент `HRDescription` содержит информацию, отображаемую в окне отладчика.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Элемент UIVisualizer
Элемент `UIVisualizer` регистрирует подключаемый модуль графического визуализатора в отладчике. Графический визуализатор создает диалоговую коробку или другой интерфейс, который показывает переменную или объект таким образом, чтобы соответствовать типу данных. Плагин visualizer должен быть автором как [VSPackage](../extensibility/internals/vspackages.md)и должен предоставить услугу, которую может потреблять отладчик. Файл *.natvis* содержит регистрационную информацию для плагина, например, его имя, GUID экспонируемой службы и типы, которые он может визуализировать.

Здесь приведен пример элемента UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId`  -  Пара `Id` атрибутов определяет `UIVisualizer`. Это `ServiceId` GUID службы визуализатор пакет предоставляет. `Id`является уникальным идентификатором, который отличает визуализаторы, если служба предоставляет более одного. В предыдущем примере один и тот же сервис визуализаторов предоставляет два визуализатора.

- Атрибут `MenuName` определяет имя визуализатора для отображения в выпадении вниз рядом с значком увеличительного стекла в отладчике. Пример:

  ![Контекстное меню UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Контекстное меню UIVisualizer")

Каждый тип, определенный в файле *.natvis,* должен явно перечислять любые визуализаторы uI, которые могут отображать его. Отладчик сопоставляет ссылки визуализаторов в записях типа с зарегистрированными визуализаторами. Например, запись следующего `std::vector` типа `UIVisualizer` для ссылок в предыдущем примере.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Вы можете увидеть пример `UIVisualizer` расширения [Image Watch,](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) используемого для просмотра битовых карт в памяти.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Элемент CustomVisualizer
 `CustomVisualizer`является точкой расширения, которая определяет расширение VSIX, которое вы пишете для управления визуализациями в коде Visual Studio. Для получения дополнительной информации о написании расширений VSIX, [см.](../extensibility/visual-studio-sdk.md)

Это гораздо больше работы, чтобы написать пользовательский визуализатор, чем определение XML Natvis, но вы свободны от ограничений о том, что Natvis делает или не поддерживает. Пользовательские визуализаторы имеют доступ к полному набору AUP, расширяющих отладоть, которые могут задавить запрос и изменение процесса отладки или общаться с другими частями Visual Studio.

 Вы можете `Condition`использовать, `IncludeView` `ExcludeView` и атрибуты на `CustomVisualizer` элементах.

 ## <a name="limitations"></a>Ограничения

Настройки Natvis работают с классами и структурами, но не набирают.

Natvis не поддерживает визуализаторы для `int` `bool`примитивных типов (например, ) или для указателей на примитивные типы. В этом сценарии одним из вариантов является использование [спецификации формата,](../debugger/format-specifiers-in-cpp.md) подходящей для случая использования. Например, если `double* mydoublearray` вы используете в коде, то можно использовать спецификацию формата массива в окне **часов оговора,** например выражение, `mydoublearray, [100]`отображая первые 100 элементов.

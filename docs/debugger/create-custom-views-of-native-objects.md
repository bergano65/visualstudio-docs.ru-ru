---
title: Создание пользовательских представлений для объектов C++
description: Использование платформы Natvis для настройки способа отображения собственных типов в отладчике в Visual Studio
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 5a219ae5257bce2a84dc17556939a44ecb02dcce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857744"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Создание пользовательских представлений для объектов C++ в отладчике с помощью платформы Natvis

Платформа Visual Studio *Natvis* позволяет настраивать способ отображения собственных типов в окнах переменных отладчика, таких как **Локальные** и **Контрольные значения**, а также **DataTips**. Визуализации Natvis улучшают отображение создаваемых типов во время отладки.

Natvis заменяет файл *autoexp.dat* в предыдущих версиях Visual Studio синтаксисом XML и обеспечивает улучшенную диагностику, управление версиями и поддержку нескольких файлов.

> [!NOTE]
> Настройки Natvis работают с классами и структурами, но не с определениями типов.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Визуализации Natvis

Платформу Natvis можно использовать для создания правил визуализации для создаваемых типов, чтобы разработчики могли легко получить к ним доступ во время отладки.

Например, на рисунке ниже показана переменная типа [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) в окне отладчике без применения дополнительных пользовательских визуализаций.

![Визуализация элемента TextBox по умолчанию](../debugger/media/dbg_natvis_textbox_default.png "Визуализация элемента TextBox по умолчанию")

В выделенной строке показано свойство `Text` класса `TextBox`. Поиск этого свойства затруднен из-за сложной иерархии классов. Отладчик не знает, как интерпретировать тип пользовательской строки, поэтому вы не видите строку, находящуюся внутри текстового поля.

Тот же тип объекта `TextBox` выглядит гораздо проще в окне переменных, когда применяются пользовательские правила визуализации Natvis. Важные члены класса отображаются вместе, и отладчик может показывать базовое строковое значение типа настраиваемой строки.

![Данные TextBox с использованием визуализатора](../debugger/media/dbg_natvis_textbox_visualizer.png "Данные TextBox с использованием визуализатора")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Использование NATVIS-файлов в проектах C++

Natvis использует *NATVIS*-файлы для указания правил визуализации. *NATVIS*-файл — это XML-файл с расширением *NATVIS*. Схема Natvis определена в папке *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Основной структурой *NATVIS*-файла является один элемент `Type` или несколько, представляющих записи визуализации. Полное имя каждого элемента `Type` задается в его атрибуте `Name`.

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

В Visual Studio некоторые *NATVIS*-файлы доступны в папке *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*. Эти файлы имеют правила визуализации для многих распространенных типов и могут служить примерами для написания визуализаций для новых типов.

### <a name="add-a-natvis-file-to-a-c-project"></a>Добавление NATVIS-файла в проект C++

Вы можете добавить *NATVIS*-файл в любой проект на языке C++.

**Добавление нового *NATVIS*-файла**

1. Выберите узел проекта C++ в **обозревателе решений**, выберите **Проект** > **Добавить новый элемент** или щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** последовательно выберите **Visual C++**  > **Служебная программа** > **Файл визуализации отладчика (NATVIS)** .

1. Присвойте файлу имя и нажмите кнопку **Добавить**.

   Новый файл добавляется в **обозреватель решений** и открывается в области документа Visual Studio.

Отладчик Visual Studio автоматически загружает *NATVIS*-файлы в проекты C++ и по умолчанию включает их в *PDB*-файл при сборке проекта. При отладке приложения сборки отладчик загружает *NATVIS*-файл из *PDB*-файла, даже если проект не открыт. Если вам не нужен *NATVIS*-файл, включенный в *PDB*-файл, его можно исключить из созданного *PDB*-файла.

**Исключение *NATVIS*-файла из *PDB*-файла**

1. В *обозревателе решений* выберите **NATVIS**-файл и щелкните значок **Свойства** либо щелкните файл правой кнопкой мыши и выберите пункт **Свойства**.

1. Разверните список **Исключено из сборки** и выберите **Да**, а затем нажмите кнопку **OK**.

>[!NOTE]
>Для отладки исполняемых проектов используйте элементы решений в целях добавления любых *NATVIS*-файлов, которые отсутствуют в *PDB*-файле, так как нет доступных проектов C++.

>[!NOTE]
>Правила Natvis, которые загружаются из *PDB*-файла, применяются только к типам в модуле, к которому относится *PDB*-файл. Например, если в файле *Module1.pdb* есть запись Natvis для типа с именем `Test`, эта запись применяется только к классу `Test` в библиотеке *Module1.dll*. Если в другом модуле также определен класс с именем `Test`, запись Natvis в *Module1.pdb* к нему не применяется.

**Установка и регистрация *NATVIS*-файла с помощью пакета VSIX**

С помощью пакета VSIX можно устанавливать и регистрировать *NATVIS*-файлы. Независимо от места установки все зарегистрированные *NATVIS*-файлы автоматически выбираются во время отладки.

1. Включите *NATVIS*-файл в пакет VSIX. Например, для следующего файла проекта:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Зарегистрируйте *NATVIS*-файл в файле *source.extension.vsixmanifest*.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Расположения файлов Natvis

Если *NATVIS*-файлы необходимо применить к нескольким проектам, их можно добавить в каталог пользователя или системный каталог.

*NATVIS*-файлы определяются в следующем порядке.

1. Любые *NATVIS*-файлы, встроенные в отлаживаемый *PDB*-файл (если файл с тем же именем не существует загруженном проекте).

2. Любые *NATVIS*-файлы, являющиеся частью загруженного проекта C++ или решения верхнего уровня. В эту группу входят все загруженные проекты C++, включая библиотеки классов, но не проекты на других языках.

3. Любые *NATVIS*-файлы, установленные и зарегистрированные с помощью пакета VSIX.

::: moniker range="vs-2017"

4. Каталог Natvis конкретного пользователя (например, *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Каталог Natvis конкретного пользователя (например, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Каталог Natvis всей системы ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). В этом каталоге находятся *NATVIS*-файлы, которые устанавливаются вместе с Visual Studio. При наличии прав администратора в этот каталог можно добавить другие файлы.

## <a name="modify-natvis-files-while-debugging"></a>Изменение NATVIS-файлов во время отладки

Вы можете изменить *NATVIS*-файл в IDE во время отладки проекта. Откройте файл в том же экземпляре Visual Studio, с помощью которого выполняется отладка, измените и сохраните его. Сразу после сохранения файла окна **Контрольные значения** и **Локальные** должны обновиться в соответствии с изменениями.

Вы также можете добавить или удалить *NATVIS*-файлы в отлаживаемом решении, и Visual Studio добавит или удалит соответствующие визуализации.

Вы не можете обновить *NATVIS*-файлы, внедренные в *PDB*-файлы, во время отладки.

Если вы измените *NATVIS*-файл вне Visual Studio, изменения не вступят в силу автоматически. Для обновления окон отладчика можно заново выполнить команду **.natvisreload** в окне **Интерпретация**. В результате изменения вступят в силу без перезапуска сеанса отладки.

Кроме того, команда **.natvisreload** позволяет обновить *NATVIS*-файл до более новой версии. Например, *NATVIS*-файл может быть возвращен в систему управления версиями, и вам нужно выбрать последние изменения, внесенные другим пользователем.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Выражения и форматирование
Визуализации Natvis используют выражения C++ для указания элементов данных для отображения. В дополнение к усовершенствованиям и ограничениям выражений C++ в отладчике, описанных в статье [Оператор контекста (C++)](../debugger/context-operator-cpp.md), необходимо учитывать следующие различия.

- Выражения Natvis вычисляются в контексте визуализируемого объекта, а не текущего кадра стека. Например, `x` в выражении Natvis ссылается на поле с именем **x** в визуализируемом объекте, а не на локальную переменную с именем **x** в текущей функции. Локальные переменные недоступны в выражениях Natvis, хотя доступны глобальные переменные.

- Выражения Natvis не позволяют выполнять вычисление функции или реализовать побочные эффекты. Вызовы функций и операторы присваивания игнорируются. Поскольку [встроенные функции отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) не зависимы от побочных эффектов, их можно свободно вызывать из любого выражения Natvis, даже если другие вызовы функций запрещены.

- Для управления отображением выражения можно использовать любой из описателей формата, описанных в статье [Описатели формата в C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Описатели формата пропускаются, когда запись используется Natvis внутренним образом, например выражение `Size` в [расширении ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

>[!NOTE]
> Поскольку документ Natvis имеет формат XML, в выражениях не удастся напрямую использовать такие операторы, как знак амперсанда, знак больше, знак меньше или оператор сдвига. Эти символы должны быть экранированы как в теле элемента, так и в операторах условия. Пример:<br>
> \<Item Name="HiByte"\>(byte)(_flags \&gt;\&gt; 24),x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>"None"\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>"Some"\</Item\>

## <a name="natvis-views"></a>Представления Natvis

Можно определить различные представления Natvis для отображения типов различными способами. Например, ниже приведена визуализация `std::vector`, которая определяет упрощенное представление с именем `simple`. Элементы `DisplayString` и `ArrayItems` отображаются в представлении по умолчанию и представлении `simple`, а элементы `[size]` и `[capacity]` не отображаются в представлении `simple`.

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

В окне **Контрольные значения** можно использовать описатель формата **,view** для указания альтернативного представления. Простое представление отображается как **vec,view(simple)** .

![Окно контрольных значений с простым представлением](../debugger/media/watch-simpleview.png "Окно контрольных значений с простым представлением")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Ошибки Natvis

Когда отладчик обнаруживает ошибки в записи визуализации, он пропускает их. Он либо отображает тип в его необработанном виде, либо выбирает другую подходящую визуализацию. С помощью диагностики Natvis можно понять, почему отладчик проигнорировал запись визуализации, и просмотреть базовые ошибки синтаксиса и анализа.

**Включение диагностики Natvis**

- Последовательно выберите **Сервис** > **Параметры** (или **Отладка** > **Параметры**) > **Отладка** > **Окно вывода**, задайте в качестве значения параметра **Диагностические сообщения Natvis (только C++)** **Ошибка**, **Предупреждение** или **Подробно**, а затем нажмите кнопку **OK**.

Ошибки появляются в окне **Вывод**.

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

Элемент `AutoVisualizer` может иметь дочерние элементы [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer) и [CustomVisualizer](#BKMK_CustomVisualizer).

### <a name="type-element"></a><a name="BKMK_Type"></a> Элемент Type

Базовый элемент `Type` выглядит следующим образом.

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Элемент `Type` определяет следующее.

1. Для какого типа должна использоваться эта визуализация (атрибут `Name`).

2. Как должно выглядеть значение объекта этого типа (элемент `DisplayString`).

3. Как должны выглядеть члены типа, когда пользователь раскрывает тип в окне переменной (узел `Expand`).

#### <a name="templated-classes"></a>Шаблонные классы
Атрибут `Name` элемента `Type` принимает символ звездочки `*` как подстановочный знак, который можно использовать для имен шаблонных классов.

В следующем примере используется та же визуализация, независимо от того, представляет ли объект собой `CAtlArray<int>` или `CAtlArray<float>`. Если есть специальная запись визуализации для `CAtlArray<float>`, она имеет приоритет над универсальной.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

На параметры шаблона можно ссылаться в записи визуализации с помощью макросов $T1, $T2 и т. д. Чтобы найти примеры этих макросов, см. *NATVIS*-файлы, поставляемые в комплекте с Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Сопоставление типов визуализатора
Если запись визуализации не удается подтвердить, используется следующая доступная визуализация.

#### <a name="inheritable-attribute"></a>Атрибут Inheritable
С помощью необязательного атрибута `Inheritable` можно указать, применяется ли визуализация только к базовому типу или к базовому типу и всем производным типам. Значением свойства `Inheritable` по умолчанию является `true`.

В следующем примере визуализация применяется только к типу `BaseClass`.

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Атрибут Priority

Необязательный атрибут `Priority` задает порядок, в котором следует использовать альтернативные определения, если не удается выполнить синтаксический анализ определения. Допустимые значения `Priority` — `Low`, `MediumLow`, `Medium`, `MediumHigh` и `High`. Значение по умолчанию — `Medium`. Атрибут `Priority` различает приоритеты только в одном *NATVIS*-файле.

В следующем примере сначала анализируется запись, соответствующая 2015 STL. Если анализ завершается ошибкой, используется альтернативная запись для версии 2013 библиотеки STL.

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
Атрибут `Optional` можно разместить на любом узле. Если не удается проанализировать часть выражения внутри необязательного узла, отладчик игнорирует этот узел, но применяет остальные правила `Type`. В следующем типе `[State]` является обязательным, а `[Exception]` — необязательным.  Если у `MyNamespace::MyClass` есть поле с именем _`M_exceptionHolder`, отображаются оба узла — `[State]` и `[Exception]`, но, если поле `_M_exceptionHolder` отсутствует, отображается только узел `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Атрибут Condition

Необязательный атрибут `Condition` доступен для многих элементов визуализации и определяет, когда следует использовать правило визуализации. Если выражение внутри атрибута условия разрешается в `false`, правило визуализации не применяется. Если оно разрешается в `true` или атрибут `Condition` отсутствует, визуализация применяется. Этот атрибут можно использовать для логики if-else в записях визуализации.

Например, следующая визуализация содержит два элемента `DisplayString` для типа интеллектуального указателя. Если первый член `_Myptr` пуст, условие первого элемента `DisplayString` разрешается в `true` и отображается форма. Если элемент `_Myptr` не пуст, условие вычисляется как `false`, и отображается второй элемент `DisplayString`.

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

Атрибуты `IncludeView` и `ExcludeView` указывают элементы, которые должны отображаться или не отображаться в конкретных представлениях. Например, в следующей спецификации Natvis `std::vector` в представлении `simple` не отображаются элементы `[size]` и `[capacity]`.

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

Атрибуты `IncludeView` и `ExcludeView` можно использовать для типов, а также для отдельных членов.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Элемент Version
Элемент `Version` ограничивает запись визуализации конкретным модулем и версией. Элемент `Version` помогает избежать конфликтов имен, сокращает число непреднамеренных несоответствий и позволяет использовать различные визуализации для разных версий типов.

Если общий файл заголовка, используемый различными модулями, определяет тип, версионная визуализация отображается только в том случае, когда тип находится в указанной версии модуля.

В следующем примере визуализация применима только для типа `DirectUI::Border`, входящего в `Windows.UI.Xaml.dll` в версиях с 1.0 по 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Требуется только один из атрибутов: `Min` или `Max`. Это необязательные атрибуты. Подстановочные знаки не поддерживаются.

Атрибут `Name` имеет формат *filename.ext*, например *Hello.exe* или *some.dll*. Имена путей не допускаются.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> Элемент DisplayString
Элемент `DisplayString` указывает строку, которая будет отображаться как значение переменной. Принимает произвольные строки в сочетании с выражениями. Весь код внутри фигурных скобок интерпретируется как выражение. Например, запись `DisplayString`

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

означает, что переменные типа `CPoint` отображаются, как показано на рисунке ниже.

 ![Использование элемента DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Использование элемента DisplayString")

В выражении `DisplayString` `x` и `y`, которые являются членами `CPoint`, находятся внутри фигурных скобок, и поэтому их значения вычисляются. В примере также показано, как можно экранировать фигурную скобку путем использования двойных фигурных скобок (`{{` или `}}`).

> [!NOTE]
> Элемент `DisplayString` является единственным элементом, который принимает произвольные строки и синтаксис фигурных скобок. Все остальные элементы визуализации принимают только выражения, которые может вычислять отладчик.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> Элемент StringView

Элемент `StringView` определяет значение, которое отладчик может отправить во встроенный визуализатор текста. Например, предположим, что имеется следующая визуализация для типа `ATL::CStringT`.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Объект `CStringT` отображается в окне переменных, как в следующем примере.

![Элемент CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Элемент CStringT DisplayString")

Добавление элемента `StringView` сообщает отладчику, что он может отображать значение как визуализацию текста.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Во время отладки можно выбрать значок лупы рядом с переменной, а затем выбрать **Визуализатор текста** для отображения строки, на которую указывает **m_pszData**.

 ![Данные CStringT с визуализатором StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Данные CStringT с визуализатором StringView")

Выражение `{m_pszData,su}` содержит спецификатор формата C++ (**su**), чтобы значение отображалось как строка Юникода. Дополнительные сведения см. в статье [Описатели формата в C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Элемент Expand

Необязательный узел `Expand` настраивает дочерние элементы визуализированного типа при развертывании типа в окне переменной. Узел `Expand` принимает список дочерних узлов, которые определяют дочерние элементы.

- Если узел `Expand` не определен в записи визуализации, дочерние элементы используют правила расширений по умолчанию.

- Если узел `Expand` указан без дочерних узлов в нем, тип нельзя развернуть в окнах отладчика.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Расширение элемента

 Элемент `Item` — самый простой и самый распространенный элемент в узле `Expand`. `Item` определяет один дочерний элемент. Например, класс `CRect` с полями `top`, `left`, `right` и `bottom` имеет следующую запись визуализации.

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

В окне отладчика тип `CRect` выглядит как в следующем примере.

![CRect с расширением элемента Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect с расширением элемента Item")

Отладчик вычисляет выражения, указанные в элементах `Width` и `Height`, и выводит значения в столбце **Значение** окна переменной.

Отладчик автоматически создает узел **[базовое представление]** для каждого пользовательского расширения. На предыдущем снимке экрана отображается развернутый узел **[базовое представление]** , чтобы показать отличие базового представления по умолчанию объекта от его визуализации Natvis. Расширение по умолчанию создает поддерево для базового класса и перечисляет все данные-члены базового класса в качестве дочерних элементов.

> [!NOTE]
> Если выражение элемента указывает на сложный тип, сам узел **Item** можно будет развернуть.

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

Узел `ArrayItems` должен иметь следующее.

- Выражение `Size` (которое должно вычисляться с получением целого числа) для отладчика, чтобы понять длину массива.
- Выражение `ValuePointer`, которое указывает на первый элемент (который должен быть указателем типа элемента, отличного от `void*`).

Значение по умолчанию нижней границы массива — 0. Чтобы переопределить это значение, используйте элемент `LowerBound`. Примеры приведены в *NATVIS*-файлах, поставляемых с Visual Studio.

>[!NOTE]
>Оператор `[]` (например, `vector[i]`) можно использовать с любой визуализацией одномерного массива, которая использует `ArrayItems`, даже если сам тип (например, `CATLArray`) не допускает использование этого оператора.

Можно также определить многомерные массивы. В этом случае отладчику требуется немного больше информации для правильного отображения дочерних элементов.

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

- `Direction` определяет, имеет ли массив порядок, основанный на строках или столбцах.
- `Rank` указывает ранг массива.
- Элемент `Size` принимает неявный параметр `$i`, вместо которого подставляет индекс измерения для нахождения длины массива в этом измерении. В предыдущем примере выражение `_M_extent.M_base[0]` должно выдавать длину нулевого измерения, `_M_extent._M_base[1]` — первого и так далее.

Здесь приводится пример того, как двумерный объект `Concurrency::array` выглядит в окне отладчика.

![Двумерный массив с расширением ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Двумерный массив с расширением ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Расширение IndexListItems

Расширение `ArrayItems` можно использовать только в том случае, если элементы массива располагаются в памяти непрерывно. Отладчик переходит к следующему элементу, просто увеличивая свой указатель. Для управления индексом в узле значения используйте узлы `IndexListItems`. Здесь приводится визуализация, использующая узел `IndexListItems`.

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

Единственное различие между `ArrayItems` и `IndexListItems` состоит в том, что `ValueNode` ожидает полного выражения до i<sup></sup>-го элемента с неявным параметром `$i`.

>[!NOTE]
>Оператор `[]` (например, `vector[i]`) можно использовать с любой визуализацией одномерного массива, которая использует `IndexListItems`, даже если сам тип (например, `CATLArray`) не допускает использование этого оператора.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Расширение LinkedListItems

Если визуализированный тип представляет связанный список, отладчик может отображать его дочерние элементы с помощью узла `LinkedListItems` . Следующая визуализация для типа `CAtlList` использует `LinkedListItems`.

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

Отладчик вычисляет выражения `NextPointer` и `ValueNode` в контексте элемента узла `LinkedListItems`, а не родительского типа списка. В предыдущем примере у `CAtlList` есть класс `CNode` (находящийся в `atlcoll.h`), являющийся узлом связанного списка. `m_pNext` и `m_element` — поля этого класса `CNode`, а не класса `CAtlList`.

`ValueNode` можно оставить пустым или использовать `this` для ссылки на сам узел `LinkedListItems`.

#### <a name="customlistitems-expansion"></a>Расширение LinkedListItems

Расширение `CustomListItems` позволяет записывать настраиваемую логику для обхода структуры данных, например хэш-таблицы. Используйте `CustomListItems` для визуализации структур данных, в которых все, что нужно вычислить, можно выразить через выражения C++, но не вполне подходит под определение `ArrayItems`, `IndexListItems` или `LinkedListItems`.

`Exec` можно использовать для выполнения кода внутри расширения `CustomListItems` с помощью переменных и объектов, определенных в расширении. С `Exec` можно использовать логические операторы, арифметические операторы и операторы присваивания. `Exec` нельзя применять для вычисления функций, за исключением [встроенных функций отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state), поддерживаемых вычислителем выражений C++.

Следующий визуализатор для `CAtlMap` является отличным примером подходящих ситуаций для использования `CustomListItems`.

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
 Если визуализированный тип представляет дерево, отладчик может пройти дерево отображать его дочерние элементы с помощью узла `TreeItems` . Здесь приводится визуализация для типа `std::map` с помощью узла `TreeItems`.

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

Синтаксис очень похож на узел `LinkedListItems`. `LeftPointer`, `RightPointer` и `ValueNode` вычисляются в контексте класса узла дерева. `ValueNode` можно оставить пустым или использовать `this` для ссылки на сам узел `TreeItems`.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Расширение ExpandedItem
 Элемент `ExpandedItem` создает агрегированное дочернее представление путем отображения свойств базовых классов или данных-членов так, как будто они являются дочерними элементами визуализируемого типа. Отладчик вычисляет указанное выражение и добавляет дочерние узлы результата в список дочерних элементов визуализируемого типа.

Например, тип интеллектуального указателя `auto_ptr<vector<int>>` обычно отображается следующим образом.

 ![Расширение по умолчанию — auto&#95;ptr&#60;vector&#60;int&#62;&#62;](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Расширение по умолчанию")

 Чтобы просмотреть значения вектора, необходимо развернуть два уровня в окне переменных, проходя через член `_Myptr`. При добавлении элемента `ExpandedItem` можно исключить переменную `_Myptr` из иерархии и просмотреть непосредственно элементы вектора elements:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Расширение ExpandedItem — auto&#95;ptr&#60;vector&#60;int&#62;&#62;](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Расширение ExpandedItem")

В следующем примере показано, как агрегировать свойства из базового класса в производный класс. Предположим, класс `CPanel` является производным от `CFrameworkElement`. Вместо повторения свойств, полученных из базового класса `CFrameworkElement`, визуализация узла `ExpandedItem` добавляет эти свойства в дочерний список класса `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Здесь необходим спецификатор формата **nd**, который отключает сопоставление визуализации для производного класса. В противном случае выражение `*(CFrameworkElement*)this` приведет к тому, что визуализация `CPanel` будет применена снова, поскольку правила сопоставления типов визуализации по умолчанию считают ее наиболее подходящей. Использование спецификатора формата **nd** дает отладчику указание использовать визуализацию базового класса или расширение по умолчанию базового класса, если базовый класс не имеет визуализации.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Расширение синтетического элемента
 Там, где элемент `ExpandedItem` предоставляет более плоское представление данных, устраняя иерархии, узел `Synthetic` делает обратное. Он позволяет создать искусственный дочерний элемент, который не является результатом выражения. Искусственный элемент может иметь собственные дочерние элементы. В следующем примере визуализация для типа `Concurrency::array` использует узел `Synthetic` , чтобы показать диагностическое сообщение пользователю.

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

 ![Concurrency::Array с расширением элемента Synthetic](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array с расширением элемента Synthetic")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> Элемент HResult
 Элемент `HResult` позволяет настраивать сведения, которые отображаются для **HRESULT** в окнах отладчика. Элемент `HRValue` должен содержать 32-разрядное значение **HRESULT**, который требуется настроить. Элемент `HRDescription` содержит сведения для отображения в окне отладчика.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> Элемент UIVisualizer
Элемент `UIVisualizer` регистрирует подключаемый модуль графического визуализатора в отладчике. Графический визуализатор создает диалоговое окно или другой интерфейс, который отображает переменную или объект в соответствии с его типом данных. Подключаемый модуль визуализатора должен быть создан как [VSPackage](../extensibility/internals/vspackages.md) и должен предоставлять службу, которая может использоваться отладчиком. *NATVIS*-файл содержит информацию о регистрации подключаемого модуля, например имя, GUID предоставляемой службы, а также типы, которые он может визуализировать.

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

- Пара атрибутов `ServiceId` - `Id` определяет `UIVisualizer`. `ServiceId` является идентификатором GUID службы, предоставляемой пакетом визуализатора. `Id` является уникальным идентификатором, отличающим визуализаторы, если служба предоставляет несколько визуализаторов. В предыдущем примере та же служба визуализатора предоставляет два визуализатора.

- Атрибут `MenuName` определяет имя визуализатора, которое будет отображаться в раскрывающемся списке рядом со значком лупы в отладчике. Пример:

  ![Контекстное меню UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Контекстное меню UIVisualizer")

Каждый тип, определенный в *NATVIS*-файле, должен явно указать визуализаторы пользовательского интерфейса, которые могут отображать их. Отладчик сопоставляет ссылки на визуализаторы в записях типов для сопоставления типов с зарегистрированными визуализаторами. Например, следующая запись типа для `std::vector` ссылается на `UIVisualizer` в предыдущем примере.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Пример `UIVisualizer` см. в расширении [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance), используемом для просмотра находящихся в памяти растровых изображений.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Элемент CustomVisualizer
 `CustomVisualizer` — это точка расширяемости, указывающая расширение VSIX, которое можно написать для управления визуализациями в коде Visual Studio. Дополнительные сведения о создании расширений VSIX см. в статье [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

Написание настраиваемого визуализатора гораздо сложнее, чем написание XML-определения Natvis, но с ним не связаны ограничения поддержки Natvis. Настраиваемые визуализаторы имеют доступ к полному набору API-интерфейсов расширяемости отладчика, которые можно использовать для запроса и изменения отлаживаемого процесса или взаимодействия с другими частями Visual Studio.

 Для элементов `CustomVisualizer` можно использовать атрибуты `Condition`, `IncludeView` и `ExcludeView`.

## <a name="limitations"></a>Ограничения

Настройки Natvis работают с классами и структурами, но не с определениями типов.

Natvis не поддерживает визуализаторы для примитивных типов (например, `int`, `bool`) или для указателей на примитивные типы. В этом сценарии одним из вариантов является использование подходящего [описателя формата](../debugger/format-specifiers-in-cpp.md). Например, если в коде используется `double* mydoublearray`, в окне **Контрольное значение** отладчика можно использовать описатель формата массива, например выражение `mydoublearray, [100]`, которое показывает первые 100 элементов.

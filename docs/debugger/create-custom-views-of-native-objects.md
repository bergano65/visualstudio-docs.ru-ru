---
title: Создание пользовательских представлений для объектов C++
description: Платформу Natvis можно использовать для настройки способа, что Visual Studio отображает собственные типы в отладчике
ms.date: 10/31/2018
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
ms.openlocfilehash: 2dba61d53bdb0007eb2a4f0acff734613e320ab9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649645"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger"></a>Создание пользовательских представлений C++ объектов в отладчике

В Visual Studio *Natvis* framework настраивает способ собственных типов отображаются в окнах переменных отладчика, такие как **"Локальные"** и **Watch** windows и в **Подсказок по данным**. Визуализации Natvis позволяют типов, которые можно создать более видимым во время отладки.

Natvis заменяет *autoexp.dat* файл в более ранних версиях Visual Studio с помощью синтаксиса XML, улучшенную диагностику, управление версиями, а несколько поддержки.

## <a name="BKMK_Why_create_visualizations_"></a>Визуализации Natvis

Платформу Natvis можно использовать для создания правил визуализации для типов, что вы создаете, таким образом, разработчики могут видеть их проще во время отладки.

Например, на следующем рисунке показан переменной типа [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) в окне отладчика без применения дополнительных пользовательских визуализаций.

![Текстовое поле по умолчанию визуализации](../debugger/media/dbg_natvis_textbox_default.png "визуализации текстового поля по умолчанию")

В выделенной строке показано свойство `Text` класса `TextBox` . Сложная иерархия класса затрудняет поиск этого свойства. Отладчик не знает, как интерпретировать тип настраиваемой строки, поэтому мы не видим строку, находящуюся внутри текстового поля.

Же `TextBox` выглядит гораздо проще в окне переменных, при применении правил Natvis пользовательский визуализатор. Важные члены класса появляются вместе, и отладчик может отображать базовое значение строки пользовательского строкового типа.

![Данные TextBox с использованием визуализатора](../debugger/media/dbg_natvis_textbox_visualizer.png "данные TextBox с использованием визуализатора")

##  <a name="BKMK_Using_Natvis_files"></a>Использовать natvis-файлы в проектах C++

Использует Natvis *.natvis* -файлам указывать правила визуализации. Объект *.natvis* файл представляет собой файл XML с *.natvis* расширения. Natvis схема определена в *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Базовая структура *.natvis* файла один или несколько `Type` элементов, представляющих записях визуализации. Полное имя каждого `Type` элемент указан в его `Name` атрибута.

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

Visual Studio предоставляет некоторые *.natvis* файлы в *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* папки. Эти файлы имеют правила визуализации для многих распространенных типов и могут служить примерами для написании визуализаций для новых типов.

### <a name="add-a-natvis-file-to-a-c-project"></a>Добавление natvis-файл в проект C++

Вы можете добавить *.natvis* файл в любой проект C++.

**Чтобы добавить новую *.natvis* файла:**

1. Выберите узел проекта C++ в **обозревателе решений**и выберите **проекта** > **добавить новый элемент**, или щелкните правой кнопкой мыши проект и выберите **добавить**   >  **Новый элемент**.

1. В **Добавление нового элемента** диалоговом окне выберите **Visual C++** > **служебной программы** > **файл визуализации отладчика (.natvis)**.

1. Имя файла и выберите **добавить**.

   Добавляется новый файл **обозревателе решений**и откроется в окне документа Visual Studio.

Отладчик Visual Studio загружает *.natvis* файлами в проектах C++ автоматически и по умолчанию также включает их в *.pdb* файлов при сборке проекта. При отладке сборки приложения отладчик загружает *.natvis* файла из *.pdb* файл, даже если у вас нет открыт проект. Если вы не хотите *.natvis* файл, включенный в *.pdb*, вы можете исключить из встроенных *.pdb* файл.

**Чтобы исключить *.natvis* файла из *.pdb*:**

1. Выберите *.natvis* файл **обозревателе решений**и выберите **свойства** значок, или щелкните правой кнопкой мыши файл и выберите **свойства**.

1. Раскрывающийся список со стрелкой рядом с полем **исключено из построения** и выберите **Да**, а затем выберите **ОК**.

>[!NOTE]
>Для отладки проектов исполняемых файлов, использовать элементы решения, чтобы добавить любой *.natvis* файлы, которые не находятся в *.pdb*, поскольку отсутствует проект C++.

>[!NOTE]
>Загрузить Natvis правил из *.pdb* применяются только к типам в модулях, *.pdb* ссылается на. Например если *файле Module1.pdb* содержит запись Natvis для типа с именем `Test`, он применяется только к `Test` в класс *библиотеке Module1.dll*. Если в другом модуле также определен класс с именем `Test`, *файле Module1.pdb* запись Natvis не применяется к нему.

### <a name="BKMK_natvis_location"></a> Расположение файлов Natvis

Вы можете добавить *.natvis* файлы в каталог пользователя или системный каталог, если вам нужно применить к нескольким проектам.

*.Natvis* файлы вычисляются в следующем порядке:

1. Любой *.natvis* файлы, которые внедряются в *.pdb* отладке, если файл с тем же именем существует в загруженный проект.

2. Любой *.natvis* файлов, находящихся в загруженный проект C++ или решения верхнего уровня. Сюда входят все загруженные проекты C++, включая библиотеки классов, но не проекты на других языках.

::: moniker range="vs-2017"

3.  Каталог Natvis конкретного пользователя (например, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

3.  Каталог Natvis конкретного пользователя (например, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

4.  Каталог Natvis всей системы (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). В этом каталоге есть *.natvis* файлы, которые устанавливаются вместе с Visual Studio. Если у вас есть разрешения администратора, можно добавить файлы в этот каталог.

## <a name="modify-natvis-files-while-debugging"></a>Изменение natvis-файлы во время отладки

Вы можете изменить *.natvis* файл в интегрированной среде разработки во время отладки проекта. Откройте файл в тот же экземпляр при отладке с помощью Visual Studio, измените его и сохраните его. Сразу же после сохранения, **Watch** и **"Локальные"** обновления windows в соответствии с изменениями.

Можно также добавить или удалить *.natvis* файлов в решении, отладке, и Visual Studio добавляет или удаляет соответствующие визуализации.

Не удается обновить *.natvis* файлы, которые внедряются в *.pdb* файлы во время отладки.

При изменении *.natvis* файла вне Visual Studio, изменения не вступят в силу автоматически. Для обновления окон отладчика, стоит повторно оценить **.natvisreload** в команду **Watch** окна. Затем изменения вступят в силу без перезапуска сеанса отладки.

Также используйте **.natvisreload** команду, чтобы обновить *.natvis* файла до более новой версии. Например *.natvis* файл может быть возвращен в системы управления версиями, и вы хотите получить последние изменения, внесенные.

##  <a name="BKMK_Expressions_and_formatting"></a> Выражения и форматирование
Визуализации Natvis используют выражения C++ для указания элементов данных для отображения. В дополнение к усовершенствованиям и ограничениям выражений C++ в отладчике, которые описаны в [(C++) с помощью оператора контекста](../debugger/context-operator-cpp.md), следует учитывать следующее:

- Выражения Natvis вычисляются в контексте визуализируемого объекта, а не текущего кадра стека. Например `x` в Natvis выражение ссылается на поле с именем **x** в визуализируемом объекте, не в локальную переменную с именем **x** в текущей функции. Локальные переменные в выражениях Natvis, недоступны, хотя доступны глобальные переменные.

- Выражения Natvis не позволяют вычисление функции или побочные эффекты. Вызовы функций и операторы присваивания игнорируются. Поскольку [встроенные функции отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) не зависимы от побочных эффектов, их можно свободно вызывать из любого выражения Natvis, даже если другие вызовы функций запрещены.

- Чтобы управлять отображением выражения, можно использовать любые спецификаторы формата, описанные в [описателях в C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Спецификаторы формата пропускаются, когда операция используется внутренне Natvis, такие как `Size` выражение в [расширения ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Представления Natvis

Вы можете определить различные представления Natvis, чтобы отобразить типы по-разному. Например, вот визуализацию `std::vector` , определяющий упрощенное представление с именем `simple`. `DisplayString` И `ArrayItems` элементы отобразятся в представлении по умолчанию и `simple` представление, хотя `[size]` и `[capacity]` элементы не отображаются `simple` представления.

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

В **Watch** окно, используйте **, представление** описатель формата для указания альтернативного представления. Простое представление отображается в виде **vec,view(simple)**:

![Окно контрольных значений с простым представлением](../debugger/media/watch-simpleview.png "окно контрольных значений с простым представлением")

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Ошибок Natvis

Когда отладчик обнаруживает ошибки в записи визуализации, он игнорирует их. Он отображает тип в его необработанной форме или выбирает другую подходящую визуализацию. Диагностику Natvis можно использовать для понять, почему отладчик учитываются записи визуализации, см. в разделе базового синтаксиса и ошибок синтаксического анализа.

**Чтобы включить диагностику Natvis:**

- В разделе **средства** > **параметры** (или **Отладка** > **параметры**) > **отладки**  >  **Окно вывода**, задайте **диагностические сообщения Natvis (C++ только)** для **ошибка**, **предупреждение** , или **Verbose**, а затем выберите **ОК**.

Ошибки отображаются в **вывода** окна.

##  <a name="BKMK_Syntax_reference"></a> Справочник по синтаксису Natvis

###  <a name="BKMK_AutoVisualizer"></a> Элемент AutoVisualizer
Элемент `AutoVisualizer` — это корневой узел *NATVIS*-файла, который содержит атрибут `xmlns:` пространства имен.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer` Элемент может иметь [тип](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), и [CustomVisualizer](#BKMK_CustomVisualizer) дочерних элементов.

###  <a name="BKMK_Type"></a> Элемент Type

Базовое `Type` выглядит как в этом примере:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type` Элемент указывает:

1. Тип визуализации должен использоваться для ( `Name` атрибут).

2. Как должно выглядеть значение объекта этого типа (элемент `DisplayString` ).

3. Как должны выглядеть члены типа, когда пользователь разворачивает тип в окне переменной ( `Expand` узла).

#### <a name="templated-classes"></a>Шаблонные классы
`Name` Атрибут `Type` принимает символ звездочки `*` как подстановочный знак, который может использоваться для имен шаблонных классов.

В следующем примере используется одной визуализации, является ли объект `CAtlArray<int>` или `CAtlArray<float>`. Если имеется специальная запись визуализации для `CAtlArray<float>`, то она имеет приоритет над универсальной.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Можно ссылаться на параметры шаблона в записи визуализации с помощью макросов $t1, $T2 и так далее. Чтобы найти примеры этих макросов, см. *NATVIS*-файлы, поставляемые в комплекте с Visual Studio.

####  <a name="BKMK_Visualizer_type_matching"></a> Сопоставление типов визуализатора
Если запись визуализации не удается проверить, используется следующая доступная визуализация.

#### <a name="inheritable-attribute"></a>Атрибут Inheritable
Необязательный `Inheritable` атрибута определяет визуализации применяется только к базовому типу, или базового типа и все производные типы. Значением свойства `Inheritable` по умолчанию является `true`.

В следующем примере визуализация применяется только к `BaseClass` типа:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Атрибут Priority

Необязательный `Priority` атрибут задает порядок, в котором для использования альтернативного определений, если определение не удается выполнить синтаксический анализ. Возможные значения `Priority` являются: `Low`, `MediumLow`,`Medium`, `MediumHigh`, и `High`. Значение по умолчанию — `Medium`. `Priority` Атрибут только коррелирующего приоритетов в одном *.natvis* файла.

В следующем примере сначала анализируется записи, которая соответствует 2015 STL. Если это не удается выполнить синтаксический анализ, он использует альтернативную запись для версии STL 2013:

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
Вы можете поместить `Optional` атрибут на любом узле. Если не удается проанализировать как часть выражения в необязательном узле, отладчик пропускает этот узел, но применяется до конца `Type` правила. В следующем типе `[State]` является обязательным, а `[Exception]` — необязательным.  Если `MyNamespace::MyClass` есть поле с именем _`M_exceptionHolder`, оба `[State]` узла и `[Exception]` узел отображается, но, если не `_M_exceptionHolder` поле только `[State]` появится узел.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

###  <a name="BKMK_Condition_attribute"></a> Атрибут Condition

Необязательный `Condition` атрибут доступен для многих элементов визуализации и указывает, когда следует использовать правила визуализации. Если выражение внутри атрибута условия разрешается в `false`, не применяется правило визуализации. Если результат вычисления равен `true`, или не `Condition` визуализация применяется атрибут. Этот атрибут можно использовать для логики if-else в записях визуализации.

Например, следующая визуализация содержит два `DisplayString` элементов для типа интеллектуального указателя. Когда `_Myptr` элемент пуст, условие первого `DisplayString` сопоставляется элемент `true`, поэтому эта форма отображает. При `_Myptr` член не является пустым, условие принимает значение `false`, а второй — `DisplayString` отображает элемент.

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

`IncludeView` И `ExcludeView` атрибуты указывают элементы для отображения или не в определенных представлениях. Например, в следующем спецификацию Natvis `std::vector`, `simple` представление не отображает `[size]` и `[capacity]` элементы.

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

Можно использовать `IncludeView` и `ExcludeView` атрибуты для типов и для отдельных членов.

###  <a name="BKMK_Versioning"></a> Элемент Version
`Version` Элемент области запись визуализации для конкретного модуля и версии. `Version` Элемент помогает избежать конфликтов имен, уменьшает вероятность случайных совпадений и позволяет различные визуальные представления для различных типов версий.

Если общего файла заголовка, используемом различными модулями определяет тип, версионная визуализация отображается, только в том случае, если тип находится в версии указанного модуля.

В следующем примере визуализация применима только для `DirectUI::Border` найти тип в `Windows.UI.Xaml.dll` с версии 1.0 до 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

###  <a name="BKMK_DisplayString"></a> Элемент DisplayString
`DisplayString` Элемент задает строковое значение для отображения в качестве значения переменной. Принимает произвольные строки в сочетании с выражениями. Весь код внутри фигурных скобок интерпретируется как выражение. Например, следующие `DisplayString` запись:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Означает, что переменных типа `CPoint` отображения как на следующем рисунке:

 ![Использование элемента DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "использование элемента DisplayString")

В `DisplayString` выражения, `x` и `y`, которые являются членами `CPoint`, находятся внутри фигурных скобок, поэтому их значения вычисляются. В примере также показано, как можно экранировать фигурную скобку путем использования двойных фигурных скобок ( `{{` или `}}` ).

> [!NOTE]
> Элемент `DisplayString` является единственным элементом, который принимает произвольные строки и синтаксис фигурных скобок. Все остальные элементы визуализации принимают только выражения, которые отладчик может вычислять.

###  <a name="BKMK_StringView"></a> Элемент StringView

`StringView` Элемент определяет значение, которое отладчик может отправлять к встроенному визуализатору текста. Например, если имеется следующая визуализация для `ATL::CStringT` типа:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT` Объекта отображается в окне переменных как в следующем примере:

![Элемент CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "элемент CStringT DisplayString")

Добавление `StringView` элемент указывает отладчику, что его можно отобразить значение в виде визуализации текста.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Во время отладки, можно выбрать значок лупы рядом с переменной и затем выберите **визуализатор текста** для отображения строки, **m_pszData** указывает.

 ![Данные CStringT с Визуализатором stringview](../debugger/media/dbg_natvis_stringview_cstringt.png "данные CStringT с Визуализатором stringview")

Выражение `{m_pszData,su}` содержит спецификатор формата C++ **su**, чтобы значение отображалось как строка Юникода. Дополнительные сведения см. в разделе [описателях в C++](../debugger/format-specifiers-in-cpp.md).

###  <a name="BKMK_Expand"></a> Разверните элемент

Необязательный `Expand` узел настраивает дочерних элементов визуализируемого типа, при развертывании тип в окне переменных. `Expand` Узел принимает список дочерних узлов, которые определяют дочерние элементы.

- Если `Expand` узла не указан в записи визуализации, дочерние элементы использовать правила расширения по умолчанию.

- Если `Expand` указан узел без дочерних узлов в нем, тип не разворачиваемые в окнах отладчика.

####  <a name="BKMK_Item_expansion"></a> Расширение элемента

 `Item` Элемент является наиболее базовый "и" common элементом `Expand` узла. `Item` определяет один дочерний элемент. Например `CRect` класс с полями `top`, `left`, `right`, и `bottom` имеет следующая запись визуализации:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

В окне отладчика `CRect` тип выглядит как в следующем примере:

![CRect с расширением элемента Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect с расширением элемента Item")

Отладчик вычисляет выражения, заданные в `Width` и `Height` элементов и показывает их в **значение** столбца в окне переменных.

Отладчик автоматически создает **[базовое представление]** узел для каждого пользовательского расширения. Отображает на предыдущем снимке экрана **[базовое представление]** развернут узел, чтобы показать, как по умолчанию базовое представление объекта отличается от его визуализации Natvis. Расширение по умолчанию создает поддерево для базового класса и перечисляются все элементы данных базового класса как дочерние элементы.

> [!NOTE]
> Если выражение элемента указывает на сложный тип **элемент** сам узел является расширяемым.

####  <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
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

![std::Vector с использованием расширения ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector с использованием расширения ArrayItems")

`ArrayItems` Узел должен иметь:

- Выражение `Size` (которое должно вычисляться с получением целого числа) для отладчика, чтобы понять длину массива.
- Объект `ValuePointer` выражение, которое указывает на первый элемент (который должен быть указателем типа элемента, который не `void*`).

Значение по умолчанию нижней границы массива — 0. Чтобы переопределить значение, используйте `LowerBound` элемент. *.Natvis* у примеры файлов, поставляемых с Visual Studio.

>[!NOTE]
>Можно использовать `[]` оператор, например `vector[i]`, с любой визуализацией одномерный массив, который использует `ArrayItems`, даже если сам тип (например `CATLArray`) не поддерживает этот оператор.

Можно также указать многомерных массивов. В этом случае отладчику требуется немного больше информации для правильного отображения дочерних элементов:

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

- `Direction` Указывает, имеет ли массив в порядке по строкам или столбцам.
- `Rank` указывает ранг массива.
- Элемент `Size` принимает неявный параметр `$i`, вместо которого подставляет индекс измерения для нахождения длины массива в этом измерении. В предыдущем примере выражение `_M_extent.M_base[0]` должно выдавать длину нулевого измерения, `_M_extent._M_base[1]` 1-й и т. д.

Вот как двумерный массив `Concurrency::array` объект выглядит в окне отладчика:

![Двумерный массив с расширением ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "двумерный массив с расширением ArrayItems")

####  <a name="BKMK_IndexListItems_expansion"></a> Расширение IndexListItems

Можно использовать `ArrayItems` расширения только в том случае, если элементы массива располагаются непрерывно в памяти. Отладчик переходит к следующему элементу, просто увеличивая свой указатель. Если необходимо манипулировать индексом узла значения, используйте `IndexListItems` узлов. Здесь приводится визуализация с `IndexListItems` узла:

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

Единственное различие между `ArrayItems` и `IndexListItems` — `ValueNode`, который ожидает полного выражения до i<sup>th</sup> элемента с неявным `$i` параметра.

>[!NOTE]
>Можно использовать `[]` оператор, например `vector[i]`, с любой визуализацией одномерный массив, который использует `IndexListItems`, даже если сам тип (например `CATLArray`) не поддерживает этот оператор.

####  <a name="BKMK_LinkedListItems_expansion"></a> Расширение LinkedListItems

Если визуализированный тип представляет связанный список, отладчик может отображать его дочерние элементы с помощью узла `LinkedListItems` . Следующая визуализация для `CAtlList` введите использует `LinkedListItems`:

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

Отладчик вычисляет `NextPointer` и `ValueNode` выражения в контексте `LinkedListItems` элемент узла, не родительского типа списка. В приведенном выше примере `CAtlList` имеет `CNode` класса (в `atlcoll.h`), являющийся узлом связанного списка. `m_pNext` и `m_element` — поля этого `CNode` класса, отличного от `CAtlList` класса.

`ValueNode` может быть пустым или используйте `this` для ссылки на `LinkedListItems` самого узла.

#### <a name="customlistitems-expansion"></a>Расширение LinkedListItems
Расширение `CustomListItems` позволяет записывать настраиваемую логику для обхода структуры данных, например хэш-таблицы. Используйте `CustomListItems` для визуализации структур данных, которые можно использовать выражения C++ для все необходимое для оценки, но не вполне подходит под определение для `ArrayItems`, `IndexListItems`, или `LinkedListItems`.

Следующие визуализатор для `CAtlMap` – прекрасный пример где `CustomListItems` подходит.

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

Можно использовать `Exec` для выполнения кода внутри класса `CustomListItems` расширения, переменные и объекты, определенные в развертывание. Можно использовать логические операторы, арифметические операторы и операторы присваивания с `Exec`. Нельзя использовать `Exec` для оценки функции.

`CustomListItems` поддерживает следующие встроенные функции:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> Расширение TreeItems
 Если визуализированный тип представляет дерево, отладчик может пройти дерево отображать его дочерние элементы с помощью узла `TreeItems` . Здесь приводится визуализация для `std::map` типа с помощью `TreeItems` узла:

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

Синтаксис аналогичен `LinkedListItems` узла. `LeftPointer`, `RightPointer`, и `ValueNode` вычисляются в контексте класса узла дерева. `ValueNode` может быть пустым или использовать `this` для ссылки на `TreeItems` самого узла.

####  <a name="BKMK_ExpandedItem_expansion"></a> Расширение ExpandedItem
 `ExpandedItem` Элемент генерирует агрегированного дочернего представления путем отображения свойств базовых классов или членов данных, как если бы они являются дочерними элементами визуализируемого типа. Отладчик вычисляет указанное выражение и добавляет дочерние узлы результата в дочерний список визуализируемого типа.

Например, тип интеллектуального указателя `auto_ptr<vector<int>>` обычно отображается как:

 ![Автоматическое&#95;ptr&#60;вектор&#60;int&#62; &#62; расширение по умолчанию](../debugger/media/dbg_natvis_expand_expandeditem_default.png "расширение по умолчанию")

 Чтобы просмотреть значения вектора, необходимо два уровня в окне переменных, обрабатываемым `_Myptr` член. При добавлении элемента `ExpandedItem` можно исключить переменную `_Myptr` из иерархии и просмотреть непосредственно элементы вектора elements:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Автоматическое&#95;ptr&#60;вектор&#60;int&#62; &#62; расширение expandeditem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "расширение expandeditem")

В следующем примере показано, как добавлять свойства из базового класса в производном классе. Предположим, класс `CPanel` является производным от `CFrameworkElement`. Вместо повторения свойств, полученных от базового `CFrameworkElement` класс, `ExpandedItem` визуализации узел добавляет эти свойства в списке дочерних `CPanel` класса.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Здесь необходим спецификатор формата **nd**, который отключает сопоставление визуализации для производного класса. В противном случае выражение `*(CFrameworkElement*)this` вызовет `CPanel` визуализации будет применена снова, поскольку правила сопоставления типов визуализации по умолчанию считают ее наиболее подходящей из них. Используйте **nd** описатель формата для дать указание использовать визуализацию базового класса или расширение по умолчанию, если базовый класс имеет нет визуализации отладчика.

####  <a name="BKMK_Synthetic_Item_expansion"></a> Расширение синтетического элемента
 Там, где элемент `ExpandedItem` предоставляет более плоское представление данных, устраняя иерархии, узел `Synthetic` делает обратное. Он позволяет создать искусственный дочерний элемент, не результат выражения. Искусственный элемент может иметь дочерние элементы свои собственные. В следующем примере визуализация для типа `Concurrency::array` использует узел `Synthetic` , чтобы показать диагностическое сообщение пользователю.

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

 ![Concurrency::Array с расширением искусственных элемента](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array с расширением искусственных элемента")

###  <a name="BKMK_HResult"></a> Элемент HResult
 `HResult` Элемент позволяет настраивать сведения, отображаемые для **HRESULT** в окнах отладчика. Элемент `HRValue` должен содержать 32-разрядное значение **HRESULT**, который требуется настроить. `HRDescription` Элемент содержит сведения для отображения в окне отладчика.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

###  <a name="BKMK_UIVisualizer"></a> Элемент UIVisualizer
Элемент `UIVisualizer` регистрирует подключаемый модуль графического визуализатора в отладчике. Графического визуализатора создает диалоговое окно или другой интерфейс, который показывает переменной или объекта способом согласуется с типом данных. Подключаемый модуль визуализатора должен быть создан как [VSPackage](../extensibility/internals/vspackages.md)и должен предоставлять службы, можно использовать отладчик. *.Natvis* файл содержит сведения о регистрации подключаемого модуля, например его имя, GUID предоставленной службы и типов, он может визуализировать.

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

- Объект `ServiceId`  -  `Id` определяет пару `UIVisualizer`. `ServiceId` — Это GUID службы визуализатора предоставляет пакет. `Id` — Это уникальный идентификатор, отличающий визуализаторов, если служба предоставляет более одного. В приведенном выше примере такая же служба визуализатора предоставляет 2 визуализатора.

- `MenuName` Атрибут определяет имя визуализатор для отображения в раскрывающемся списке рядом со значком лупы в отладчике. Пример:

  ![Контекстное меню UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "контекстное меню UIVisualizer")

Каждый тип, определенный в *.natvis* файла необходимо явно указать визуализаторы любого пользовательского интерфейса, которые можно отобразить его. Отладчик сопоставляет ссылки визуализаторов в записях типов с зарегистрированными визуализаторам. Например, следующая запись для типа `std::vector` ссылки `UIVisualizer` в предыдущем примере.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Вы можете ознакомиться с примером `UIVisualizer` в [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) расширении, используемом для просмотра в памяти растровых изображений.

### <a name="BKMK_CustomVisualizer"></a>Элемент CustomVisualizer
 `CustomVisualizer` — Это точка расширяемости, указывающая расширение VSIX, которое можно написать для управления визуализации в Visual Studio code. Дополнительные сведения о создании расширений VSIX см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

Это гораздо больше усилий для написания пользовательский визуализатор, чем определение XML Natvis, но свободны от ограничений, о чем Natvis или не поддерживает. Настраиваемые визуализаторы имеют доступ к полному набору расширения отладчика API-интерфейсы, которые можно запрашивать и изменения отлаживаемого процесса или взаимодействия с другими частями Visual Studio.

 Можно использовать `Condition`, `IncludeView`, и `ExcludeView` атрибуты `CustomVisualizer` элементов.
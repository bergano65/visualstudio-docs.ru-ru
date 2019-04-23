---
title: Создание настраиваемых представлений собственных объектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e44e8166fb4f03f28d96203dc7efc09d3913224c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086199"
---
# <a name="create-custom-views-of-native-objects"></a>Создание настраиваемых представлений собственных объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Платформа Visual Studio Natvis позволяет настраивать то, как Visual Studio отображает собственные типы в окнах переменных отладчика (таких как окна **контрольных значений**, **локальных переменных**и **подсказок по данным** ).  

 Natvis заменяет файл **autoexp.dat** , который использовался в предыдущих версиях Visual Studio, и обеспечивает синтаксис XML, улучшенную диагностику, управление версиями и поддержку нескольких файлов.  

> [!NOTE]
>  Платформу Natvis нельзя использовать для визуализаций в следующих случаях:  
> 
> - при отладке проекта классического приложения Windows на C++, для которого задан **смешанный**тип отладчика;  
>   - при выполнении отладки в смешанном режиме в классическом приложении для Windows в режиме совместимости управляемого кода (**Сервис/Параметры/Отладка/Общие/Режим совместимости управляемого кода**);  
>   - при отладке классического приложения для Windows в режиме совместимости машинного кода (**Сервис/Параметры/Отладка/Общие/Режим совместимости машинного кода**).  

## <a name="BKMK_Why_create_visualizations_"></a> Зачем создавать визуализации Natvis?  
 Платформу Natvis можно использовать для создания правил визуализации для создаваемых типов, чтобы разработчики могли легко получить к ним доступ во время отладки.  

 Например, на рисунке ниже показана переменная типа [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) , отображаемая в отладчике без применения дополнительных пользовательских визуализаций.  

 ![Текстовое поле по умолчанию визуализации](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 В выделенной строке показано свойство `Text` класса `TextBox` . Сложная иерархия класса затрудняет поиск этого решения; кроме того, отладчик не знает, как интерпретировать тип настраиваемой строки, используемый объектом, поэтому мы не видим строку, находящуюся внутри текстового поля.  

 Тот же тип объекта `TextBox` выглядит гораздо проще в окне переменных, когда применяются пользовательские правила визуализации. Важные члены класса можно просматривать вместе, и отладчик может отображать базовое строковое значение типа настраиваемой строки.  

 ![Данные TextBox с использованием визуализатора](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="BKMK_Using_Natvis_files"></a> Использование файлов Natvis  
 NATVIS-файлы — это XML-файлы с расширением .natvis. Схема определена в **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 Базовая структура NATVIS-файла — это один элемент `Type` или несколько. Каждый элемент `Type` представляет запись визуализации для типа, полное имя которого указано в атрибуте `Name` .  

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

 Visual Studio предоставляет некоторые NATVIS-файлы в папке **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** . Эти файлы содержат правила визуализации для многих распространенных типов и могут служить примерами при написании визуализаций для новых типов.  

## <a name="adding-natvis-files-to-your-projects"></a>Добавление NATVIS-файлов в проекты  
 Вы можете добавить NATVIS-файлы в любой проект на языке C++.  

 Чтобы добавить новый NATVIS-файл, в открытом проекте на C++ выберите узел проектов в **обозревателе решений**и щелкните команды **Добавить — Новый элемент — Visual C++ — Служебная программа — Файл визуализации отладчика (.natvis)**. Отладчик автоматически загрузит файлы Natvis из проектов C++. По умолчанию файлы Natvis в проекте также вставляются в PDB-файл, созданный проектом. Это означает, что при отладке сборки двоичного файла с помощью этого проекта отладчик загружает файл Natvis из PDB-файла, даже если проект не открыт. Если вы не хотите включать NATVIS-файл в PDB-файл, щелкните правой кнопкой мыши NATVIS-файл в **обозревателе решений**и в окне **Свойства конфигурации** задайте для параметра **Исключен из сборки** значение **Да**.  

 Рекомендуется изменять файлы Natvis с помощью Visual Studio. Любые изменения, внесенные во время отладки, вступят в силу автоматически при сохранении файла. Вы также можете воспользоваться улучшенными возможностями редактирования из IntelliSense.  

 Файлы Natvis, которые загружаются из PDB-файла, применяются только к типам в модуле, к которому относится PDB-файл. Например, если в файле Module1.pdb определена запись для типа с именем `Test`, то эта запись применяется только к классу **Test** в библиотеке Module1.dll. Если в другом модуле также определен класс с именем **Test**, запись NATVIS в Module1.pdb к нему не применяется.  

## <a name="BKMK_natvis_location"></a> Развертывание NATVIS-файлов  
 Если NATVIS-файл относится только к типам, создаваемым в проекте Visual Studio, не нужно выполнять никаких действий; NATVIS-файл включен в PDB-файл. При этом вы можете добавить NATVIS-файлы в каталог пользователя или системный каталог, если их необходимо применить к нескольким проектам.  

 Порядок, в котором вычисляются NATVIS-файлы, таков:  

1. NATVIS-файлы, встроенные в отлаживаемый PDB-файл (если файла с тем же именем не существует загруженном проекте);  

2. NATVIS-файлы, являющиеся частью загруженных проектов на C++ или элемента решения верхнего уровня. Сюда входят все загруженные проекты на C++, включая библиотеки классов, но не проекты на других языках (например, вы не можете загрузить NATVIS-файл из проекта C#). Для исполняемых проектов следует использовать элементы решений в целях размещения любых NATVIS-файлов, которые отсутствуют в PDB-файле, так как нет доступных проектов на C++.  

3. Каталог Natvis конкретного пользователя (**%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers**)  

4. Каталог Natvis всей системы (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Сюда копируются NATVIS-файлы, которые устанавливаются вместе с Visual Studio. В этот каталог также можно добавить другие файлы при наличии прав администратора.  

## <a name="modifying-natvis-files-while-debugging"></a>Изменение NATVIS-файлов во время отладки  
 Вы можете изменить NATVIS-файл в IDE во время отладки проекта, в который он включен. Откройте файл в интегрированной среде разработки (используя тот же экземпляр Visual Studio, с помощью которого выполняется отладка), измените и сохраните его. Сразу после сохранения файла окна **контрольных значений** и **локальных переменных** должны обновиться в соответствии с изменениями. Если вы измените NATVIS-файл за пределами IDE, изменения не вступят в силу автоматически. Для обновления окон можно заново выполнить команду **.natvisreload** в окне **Контрольные значения** . В результате изменения вступят в силу без перезапуска сеанса отладки.  

 Вы также можете добавить или удалить NATVIS-файлы в отлаживаемом решении, и Visual Studio добавит или удалит соответствующие визуализации.  

 Вы не можете изменить NATVIS-файл при отладке, если он встроен в PDB-файл.  

 Команда **.natvisreload** используется при обновлении NATVIS-файла до более новой версии (например, если при записи в систему управления версиями после изменения требуется получить последние изменения, внесенные в файл другими пользователями). Рекомендуется изменять файлы Natvis с помощью XML-редактора Visual Studio.  

## <a name="BKMK_Expressions_and_formatting"></a> Выражения и форматирование  
 Визуализации Natvis используют выражения C++ для указания элементов данных для отображения. В дополнение к усовершенствованиям и ограничениям выражений C++ в отладчике, описанным в [Context Operator (C++)](../debugger/context-operator-cpp.md), следует иметь в виду следующие различия:  

- Выражения Natvis вычисляются в контексте визуализируемого объекта, а не текущего кадра стека. Например, при использовании `x` в выражении Natvis, он ссылается на поле с именем `x` в визуализируемом объекте, а не на локальную переменную с именем `x` в выполняющейся в данный момент функции. Локальные переменные недоступны в выражениях Natvis, хотя доступны глобальные переменные.  

- Выражения Natvis не позволяют выполнять вычисление функции или реализовать побочные эффекты. Это означает, что вызовы функций и операторы присваивания игнорируются. Поскольку [встроенные функции отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) не зависимы от побочных эффектов, их можно свободно вызывать из любого выражения Natvis, даже если другие вызовы функций запрещены.  

  Для управления тем, как выражение отображается в окне переменных, можно использовать любые спецификаторы формата, описанные в [описателей формата](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) раздел [описатели формата в C++](../debugger/format-specifiers-in-cpp.md) раздела. Обратите внимание, что спецификаторы формата пропускаются, когда запись виртуализации используется внутренне Natvis, такие как `Size` выражение в расширение ArrayItems.  

## <a name="natvis-views"></a>Представления Natvis  
 Представления Natvis позволяют просматривать любой тип несколькими способами. Например, можно определить представление с именем **simple** , которое создает упрощенное представление типа. Вот пример визуализации `std::vector`:  

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

 Элементы `DisplayString` и `ArrayItems` используются в представлении по умолчанию и простом представлении, а элементы `[size]` и `[capacity]` исключаются из простого представления. Можно использовать описатель формата **,view** для указания альтернативного представления. В окне **Контрольные значения** простое представление указывается как **vec,view(simple)**:  

 ![Окно контрольных значений с простым представлением](../debugger/media/watch-simpleview.png "SimpleView контрольных значений")  

## <a name="BKMK_Diagnosing_Natvis_errors"></a> Диагностика ошибок Natvis  
 Диагностику Natvis можно использовать для устранения проблем синтаксиса и ошибок синтаксического анализа. Когда отладчик обнаруживает ошибки в записи визуализации, анализ которых выполнить не удалось, он просто пропускает ошибки и указывает тип в его необработанной форме или выбирает другую подходящую визуализацию. Чтобы понять, почему определенная запись визуализации пропускается, и просмотреть соответствующие ошибки, можно включить диагностику Natvis ( **Сервис/Параметры/Отладка/Окно вывода/Диагностические сообщения Natvis (только C++)** ). Ошибки отображаются в окне **Вывод** .  

## <a name="BKMK_Syntax_reference"></a> Справочник по синтаксису Natvis  

### <a name="BKMK_AutoVisualizer"></a> Элемент AutoVisualizer  
 Элемент `AutoVisualizer`  — корневой узел NATVIS-файла, который содержит атрибут `xmlns:` пространства имен.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="BKMK_Type"></a> Элемент Type  
 Базовый элемент Type выглядит следующим образом.  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Он определяет следующее.  

1. Для какого типа должна использоваться эта визуализация (атрибут `Type Name` ).  

2. Как должно выглядеть значение объекта этого типа (элемент `DisplayString` ).  

3. Как должны выглядеть члены типа, когда пользователь раскрывает их в окне переменной (узел `Expand` ).  

   **Шаблонные классы** . Атрибут `Name` элемента `Type` принимает символ звездочки `*` как подстановочный знак, который можно использовать для имен шаблонных классов:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 В этом примере используется та же визуализация независимо от того, представляет ли объект собой `CAtlArray<int>` или `CAtlArray<float>`. Если есть специальная запись визуализации для `CAtlArray<float>` , она имеет приоритет над универсальной.  

 Обратите внимание, что на параметры шаблона можно ссылаться в записи визуализации с помощью макросов $T1, $T2 и т. д. Чтобы найти примеры этих макросов, см. NATVIS-файлы, поставляемые в комплекте с Visual Studio.  

#### <a name="BKMK_Visualizer_type_matching"></a> Сопоставление типов визуализатора  
 Если запись визуализации не удается подтвердить, используется следующая доступная визуализация.  

#### <a name="inheritable-attribute"></a>Атрибут Inheritable  
 Можно указать, применяется ли визуализация только к базовому типу или к базовому типу и всем производным типам, используя необязательный атрибут `Inheritable` . В следующем примере визуализация применяется только к типу `BaseClass` :  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Значением свойства `Inheritable` по умолчанию является `true`.  

#### <a name="priority-attribute"></a>Атрибут Priority  
 Атрибут `Priority` задает порядок, в котором используются альтернативные определения, если не удается выполнить синтаксический анализ определения. Возможные значения атрибута `Priority` : `Low`, `MediumLow`,`Medium`, `MediumHigh`и `High`, а значение по умолчанию — `Medium`.  

 Атрибут приоритета следует использовать только для различения приоритетов в одном NATVIS-файле, а не между разными файлами.  

 В следующем примере мы сначала выполним синтаксический анализ записи, которая соответствует 2015 STL, и если анализ выполнить не удастся, используем альтернативную запись для версии STL 2013:  

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

#### <a name="BKMK_Versioning"></a> Элемент Version  
 Используйте элемент `Version` для ограничения области визуализаций конкретными модулями и их версиями, чтобы свести к минимуму конфликты имен и иметь возможность использовать разные визуализации для разных версий типов. Пример:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 В этом примере визуализация применима только для типа `DirectUI::Border` , входящего в `Windows.UI.Xaml.dll` в версиях от 1.0 до 1.5. Обратите внимание, что при добавлении элементов версии область действия записи визуализации ограничивается конкретным модулем и версией, что уменьшает вероятность случайных совпадений, однако если тип определен в общем файле заголовка, используемом различными модулями, визуализация, имеющая версию, не применяется, когда тип не находится в указанном модуле.  

#### <a name="optional-attribute"></a>Атрибут Optional  
 Атрибут `Optional` может использоваться для любого узла. Если не удается выполнить анализ вложенного выражения в необязательном узле, такой узел игнорируется, однако остальное содержимое элемента Type остается действительным. В следующем типе `[State]` является обязательным, а `[Exception]` — необязательным.  Это означает, что если `MyNamespace::MyClass` содержит поле с именем _`M_exceptionHolder`, по-прежнему будут отображаться оба узла, `[State]` и `[Exception]` , но если `_M_exceptionHolder` отсутствует, будет отображаться только узел `[State]` .  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="BKMK_Condition_attribute"></a> Атрибут Condition  
 Необязательный атрибут `Condition` доступен для многих элементов визуализации и определяет, когда должно использоваться правило визуализации. Если выражение внутри атрибута условия разрешается в `false`, правило визуализации, указанное элементом, не применяется. Если значение равно true или отсутствует атрибут `Condition` , правило визуализации применяется к типу. Этот атрибут можно использовать для логики `if-else` в записях визуализации. Например, визуализация ниже включает два элемента `DisplayString` для типа интеллектуального указателя.  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Если значением первого члена `_Myptr` является `null`, условие первого элемента `DisplayString` разрешается в `true`и отображается форма. Если элемент `_Myptr` не равен `null`, состояние вычисляется как `false`, и второй элемент `DisplayString` выводится на экран.  

### <a name="includeview-and-excludeview-attributes"></a>Атрибут IncludeView и ExcludeView  
 Эти атрибуты указывают элементы, которые должны отображаться или не отображаться в различных представлениях. Для примера возьмем спецификацию Natvis `std::vector`:  

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

 В простом представлении элементы [size] и [capacity] не отображаются. Если бы мы использовали `IncludeView="simple"` вместо `ExcludeView`, элементы `[size]` и `[capacity]` отображались бы в простом представлении, а не в представлении по умолчанию.  

 Атрибуты `IncludeView` и `ExcludeView` можно использовать для типов, а также для отдельных членов.  

### <a name="BKMK_DisplayString"></a> DisplayString  
 Элемент `DisplayString` задает строку, отображаемую как значение переменной. Принимает произвольные строки в сочетании с выражениями. Весь код внутри фигурных скобок интерпретируется как выражение. Например, запись `DisplayString` как эта:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 означает, что переменные типа `CPoint` отображаются следующим образом:  

 ![Использование элемента DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 В выражении `DisplayString` `x` и `y`, которые являются членами `CPoint`, находятся внутри фигурных скобок и поэтому их значения вычисляются. Выражение также показывает, как можно экранировать фигурную скобку путем использования двойных фигурных скобок ( `{{` или `}}` ).  

> [!NOTE]
>  Элемент `DisplayString` является единственным элементом, который принимает произвольные строки и синтаксис фигурных скобок. Все остальные элементы визуализации принимают только выражения, которые вычисляются отладчиком.  

### <a name="BKMK_StringView"></a> StringView  
 Элемент `StringView` определяет выражение, значение которого будет отправлено встроенному визуализатору текста. Например, предположим, что мы имеем следующую визуализацию для типа `ATL::CStringT` .  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 Объект `CStringT` выглядит следующим образом:  

 ![CStringT DisplayString element](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Визуализация отображает объект `CStringT` в окне переменной следующим образом:  

 Добавление элемента `StringView` указывает отладчику, что это значение может быть представлено визуализацией текста:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Обратите внимание на значок лупы рядом со значением ниже. Нажатие значка запустит средство визуализации текста, которое отобразит строку, на которую указывает `m_pszData` .  

 ![Данные CStringT с Визуализатором stringview](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
>  Обратите внимание, что `{m_pszData,su}` содержит спецификатор формата C++ ( `su` ), чтобы значение отображалось как строка Юникода. Дополнительные сведения см. в разделе [Format Specifiers in C++](../debugger/format-specifiers-in-cpp.md) .  

### <a name="BKMK_Expand"></a> Expand  
 Узел `Expand` позволяет настраивать дочерние элементы визуализируемого типа, когда пользователь разворачивает его в окнах переменных. Он принимает список дочерних узлов, которые определяют дочерние элементы.  

 Узел `Expand` является необязательным.  

- Если узел `Expand` не определен в записи визуализации, используются правила расширения Visual Studio по умолчанию.  

- Если узел `Expand` указан без дочерних узлов в нем, тип нельзя будет развернуть в окнах отладчика.  

#### <a name="BKMK_Item_expansion"></a> Расширение элемента  
 Элемент `Item` — самый простой и самый распространенный элемент для использования в узле `Expand` . `Item` определяет один дочерний элемент. Например, предположим, что имеется класс `CRect` с `top`, `left`, `right`и `bottom` в качестве его полей и следующая запись визуализации:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 Тип `CRect` будет выглядеть следующим образом.  

 ![CRect с расширением элемента Item](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Выражения, заданные в элементах `Width` и `Height` , вычисляются и отображаются в столбце значений. Узел `[Raw View]` автоматически создается отладчиком всякий раз, когда используется пользовательское расширение. Он развернут на снимке экрана выше, чтобы показать, как начальное представление объекта отличается от его визуализации. Расширение Visual Studio по умолчанию создает поддерево для базового класса и перечисляет все данные-члены базового класса в качестве дочерних элементов.  

> [!NOTE]
>  Если выражение элемента указывает на сложный тип, сам узел `Item` можно будет развернуть.  

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion  
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

 ![std::Vector с использованием расширения ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Как минимум, узел `ArrayItems` должен иметь:  

1. Выражение `Size` (которое должно вычисляться с получением целого числа) для отладчика, чтобы понять длину массива  

2. Выражение `ValuePointer` , которое должно указывать на первый элемент (который должен быть указателем типа элемента, отличного от `void*`).  

   Значение по умолчанию нижней границы массива — 0. Значение можно переопределить с помощью элемента `LowerBound` (примеры можно найти в NATVIS-файлах, поставляемых с Visual Studio).  

   Теперь оператор `[]` можно использовать с расширением `ArrayItems` , например `vector[i]`. Оператор [] можно использовать с любой визуализацией в одномерном массиве, который использует `ArrayItems` или `IndexListItems`, даже если сам тип не допускает использование этого оператора (например, `CATLArray`).  

   Многомерные массивы также можно определить. В этом случае отладчику требуется немного больше информации для правильного отображения дочерних элементов:  

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

 `Direction` определяет, имеет ли массив порядок, основанный на строках или на столбцах. `Rank` указывает ранг массива. Элемент `Size` принимает неявный параметр `$i` , вместо которого подставляет индекс измерения для нахождения длины массива в этом измерении. Например, в предыдущем примере выражение `_M_extent.M_base[0]` должно выдавать длину нулевого измерения, `_M_extent._M_base[1]` — первого и так далее.  

 Здесь приводится пример того, как двумерный объект `Concurrency::array` выглядит в отладчике.  

 ![Двумерный массив с расширением ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="BKMK_IndexListItems_expansion"></a> Расширение IndexListItems  
 Можно использовать расширение `ArrayItems` только в том случае, если элементы массива располагаются в памяти непрерывно. Отладчик переходит к следующему элементу, просто увеличивая свой указатель на текущий элемент. В случаях, когда необходимо манипулировать индексом узла значения, можно использовать узлы `IndexListItems` . Здесь приводится визуализация, использующая узел `IndexListItems` .  

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

 Теперь оператор `[]` можно использовать с расширением `IndexListItems` , например `vector[i]`. Оператор `[]` можно использовать с любой визуализацией в одномерном массиве, который использует `ArrayItems` или `IndexListItems`, даже если сам тип не допускает использование этого оператора (например, `CATLArray`).  

 Единственное различие между `ArrayItems` и `IndexListItems` состоит в том, что `ValueNode` ожидает полного выражения до i<sup></sup> -того элемента с неявным параметром `$i` .  

#### <a name="BKMK_LinkedListItems_expansion"></a> Расширение LinkedListItems  
 Если визуализированный тип представляет связанный список, отладчик может отображать его дочерние элементы с помощью узла `LinkedListItems` . Здесь приводится визуализация для типа `CAtlList` с помощью этой функции:  

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

- Выражения `NextPointer` и `ValueNode` вычисляются в контексте элемента узла связанного списка, а не родительского типа связанного списка. В приведенном выше примере `CAtlList` имеет класс `CNode` (находящийся в `atlcoll.h`), представляющий узел связанного списка. `m_pNext` и `m_element` — поля этого класса `CNode` , а не класса `CAtlList` .  

- Можно оставить поле `ValueNode` пустым или использовать `this` для ссылки на сам узел связанного списка.  

#### <a name="customlistitems-expansion"></a>Расширение LinkedListItems  
 Расширение `CustomListItems` позволяет записывать настраиваемую логику для обхода структуры данных, например хэш-таблицы.  `CustomListItems` следует использовать для визуализации структур данных, в которых все, что нужно вычислить, можно выразить через выражения C++, но не вполне подходит под определение `ArrayItems`, `TreeItems`или `LinkedListItems.`.  

 Визуализатор для CAtlMap является отличным примером подходящих ситуаций для использования `CustomListItems` .  

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

#### <a name="BKMK_TreeItems_expansion"></a> Расширение TreeItems  
 Если визуализированный тип представляет дерево, отладчик может пройти дерево отображать его дочерние элементы с помощью узла `TreeItems` . Здесь приводится визуализация для типа `std::map` с помощью этой функции:  

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

 Синтаксис очень похож на узел `LinkedListItems` . `LeftPointer`, `RightPointer`и `ValueNode` вычисляются в контексте класса узла дерева, и поле `ValueNode` может оставаться пустым или иметь значение `this` , чтобы ссылаться на сам узел дерева.  

#### <a name="BKMK_ExpandedItem_expansion"></a> Расширение ExpandedItem  
 Элемент `ExpandedItem` может использоваться для создания агрегированного дочернего представления путем отображения свойств базовых классов или данных-членов так, как будто они являются дочерними элементами визуализируемого типа. Указанное выражение вычисляется, и дочерние узлы результата добавляются в список дочерних элементов визуализируемого типа. Например, предположим, что у нас есть интеллектуальный указатель типа `auto_ptr<vector<int>>` , который обычно будет отображаться следующим образом:  

 ![Автоматическое&#95;ptr&#60;вектор&#60;int&#62; &#62; расширение по умолчанию](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Чтобы просмотреть значения вектора, необходимо развернуть два уровня в окне переменных, проходя через член _Myptr. При добавлении элемента `ExpandedItem` можно исключить переменную `_Myptr` из иерархии и просмотреть непосредственно элементы вектора elements::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Автоматическое&#95;ptr&#60;вектор&#60;int&#62; &#62; расширение expandeditem](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 В следующем примере показано, как добавлять свойства из базового класса в производный класс. Предположим, класс `CPanel` является производным от `CFrameworkElement`. Вместо повторения свойств, полученных от базового класса `CFrameworkElement` , узел `ExpandedItem` позволяет присоединить эти свойства к дочернему списку класса `CPanel` . Здесь необходим спецификатор формата **nd** , который отключает сопоставление визуализации для производного класса. В противном случае выражение `*(CFrameworkElement*)this` приведет к тому, что визуализация `CPanel` будет применена снова, поскольку правила сопоставления типов визуализации по умолчанию считают ее наиболее подходящей. Использование спецификатора формата **nd** дает отладчику указание использовать визуализацию базового класса или расширение по умолчанию базового класса, если базовый класс не имеет визуализации.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="BKMK_Synthetic_Item_expansion"></a> Расширение синтетического элемента  
 Там, где элемент `ExpandedItem` предоставляет более плоское представление данных, устраняя иерархии, узел `Synthetic` делает обратное. Он позволяет создать искусственный дочерний элемент (то есть дочерний элемент, который не является результатом выражения). Этот дочерний элемент может содержать собственные дочерние элементы. В следующем примере визуализация для типа `Concurrency::array` использует узел `Synthetic` , чтобы показать диагностическое сообщение пользователю.  

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

 ![Concurrency::Array с расширением элемента sythentic](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="BKMK_HResult"></a> HResult  
 Элемент `HResult` позволяет настраивать сведения, которые отображаются для HRESULT в окнах отладчика. Элемент `HRValue` должен содержать 32-разрядное значение HRESULT, который требуется настроить. Элемент `HRDescription` содержит сведения, отображаемые в отладчике.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 Элемент `UIVisualizer` регистрирует подключаемый модуль графического визуализатора в отладчике. Подключаемый модуль графического визуализатора создает диалоговое окно или другой интерфейс для отображения переменной или объекта способом, подходящим для этого типа данных. Подключаемый модуль визуализатора должен быть создан как [VSPackage](../extensibility/internals/vspackages.md) и должен предоставлять службу, которая может использоваться отладчиком. NATVIS-файл содержит информацию о регистрации подключаемого модуля, например имя, GUID предоставляемой службы, а также типы, которые он может визуализировать.  

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

 Элемент `UIVisualizer` определяется парой атрибутов: `ServiceId` - `Id` . `ServiceId` — это GUID службы, предоставляемой пакетом визуализатора, а `Id` — уникальный идентификатор, который можно использовать для различения визуализаторов, если служба предоставляет несколько визуализаторов. В приведенном выше примере такая же служба визуализатора предоставляет 2 визуализатора.  

 Атрибут `MenuName` — это то, что пользователи видят как имя визуализатора при открытии раскрывающегося меню рядом со значком лупы в окнах переменных отладчика, например:  

 ![Контекстное меню UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Каждый тип, определенный в NATVIS–файле, должен явно указать визуализаторы пользовательского интерфейса, которые могут отображать их. Отладчик сопоставляет ссылки визуализаторов в записях типов для сопоставления типов с зарегистрированными визуализаторам. Например, следующая запись типа для `std::vector` ссылается на UIVisualizer в приведенном выше примере.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Вы увидите пример UIVisualizer в расширении Image Watch можно просматривать в памяти растровых изображений: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>Элемент CustomVisualizer  
 `CustomVisualizer` — это точка расширяемости, указывающая расширение VSIX, которое можно написать для управления визуализацией в коде, который выполняется в Visual Studio. Дополнительные сведения о создании расширений VSIX см. в разделе [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Написание настраиваемого визуализатора гораздо сложнее, чем написание XML-определения Natvis, но с ним не связаны ограничения поддержки Natvis. Настраиваемые визуализаторы имеют доступ к полному набору API-интерфейсов расширения отладчика, которые можно использовать для запроса и изменения отлаживаемого процесса или взаимодействия с другими частями Visual Studio.  

 Для элементов CustomVisualizer можно использовать атрибуты `Condition`, `IncludeView`и `ExcludeView` .

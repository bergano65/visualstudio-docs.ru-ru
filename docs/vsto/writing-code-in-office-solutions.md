---
title: Написание кода в решениях Office
description: Узнайте, как написать код в Microsoft Office решений и узнать о способе предоставления объектной модели Office управляемому коду.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b0f72e859e0847b5035e99146ef6c0435ef299d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904459"
---
# <a name="write-code-in-office-solutions"></a>Написание кода в решениях Office
  Написание кода в проектах Office и в проектах других типов в Visual Studio несколько отличается друг от друга. Многие из этих отличий связаны с тем, каким образом объектные модели Office предоставляются управляемому коду. Другие отличия связаны со структурой проектов Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Управляемый код и программирование для Office
 Основная технология, делающая возможным создание интегрированного решения Microsoft Office, — это автоматизация, которая является частью технологии объектной модели компонентов (COM). Автоматизация позволяет использовать код для создания и управления программными объектами, предоставляемыми любым приложением, библиотекой DLL или элементом ActiveX, которые поддерживают соответствующие программные интерфейсы.

### <a name="understand-primary-interop-assemblies"></a>Общие сведения о первичных сборках взаимодействия
 Приложения Microsoft Office предоставляют многие свои функциональные возможности для автоматизации. Однако непосредственно для автоматизации приложений Office управляемый код (например, Visual Basic или C#) использовать нельзя. Для автоматизации приложений Office с помощью управляемого кода необходимо использовать основные сборки взаимодействия (PIA) для Office. Основная сборка взаимодействия позволяет управляемому коду взаимодействовать с основанной на COM объектной моделью приложений Office.

 Каждое приложение Microsoft Office имеет сборку PIA. При создании проекта Office в Visual Studio ссылка на соответствующую сборку PIA автоматически добавляется в проект. Чтобы автоматизировать функции других приложений Office из проекта, необходимо вручную добавить ссылку на соответствующую сборку PIA. Дополнительные сведения см. [в разделе руководство. Назначение приложений Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Использование основных сборок взаимодействия во время разработки и в среде выполнения
 Для выполнения большинства задач разработки необходимо, чтобы основные сборки взаимодействия Office были установлены и зарегистрированы в глобальном кэше сборок на компьютере разработчика. Дополнительные сведения см. [в статье Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Наличие основных сборок взаимодействия Office на компьютере конечного пользователя для запуска решений Office, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздних версий, не требуется. Дополнительные сведения см. в статье [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Использование типов в основных сборках взаимодействия
 Основные сборки взаимодействия Office содержат комбинацию типов, предоставляющих объектную модель приложений Office и дополнительные типы инфраструктуры, которые не предназначены для прямого использования в коде. Общие сведения о типах в основных сборках взаимодействия Office см. [в разделе Общие сведения о классах и интерфейсах в основной сборке взаимодействий Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Так как типы в сборках Office PIA соответствуют типам в основанных на COM объектных моделях, способ использования этих типов часто отличается от других управляемых типов. Например, способ вызова методов, имеющих необязательные параметры, в основной сборке взаимодействия Office зависит от языка программирования, применяемого в вашем проекте. Дополнительные сведения см. в следующих разделах:

- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md).

- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Модель программ для проектов Office
 Все проекты Office содержат один или несколько созданных классов, которые предоставляют точку входа для кода. Эти классы также обеспечивают доступ к объектной модели ведущего приложения, а также доступ к функциям, например, к панелям действий и настраиваемым областям задач.

### <a name="understand-the-generated-classes"></a>Общие сведения о созданных классах
 В проектах уровня документа для Excel и Word созданный класс похож на объект верхнего уровня в объектной модели приложения. Например, созданный класс `ThisDocument` в проекте документа Word содержит те же элементы, что и класс <xref:Microsoft.Office.Interop.Word.Document> в объектной модели Word. Дополнительные сведения о созданных классах в проектах уровня документа см. в разделе [Program настроек на уровне документа](../vsto/programming-document-level-customizations.md).

 Проекты надстроек VSTO предоставляют созданный класс с именем `ThisAddIn`. Этот класс не похож на класс в объектной модели ведущего приложения. Вместо этого этот класс представляет саму надстройку VSTO и предоставляет члены, которые можно использовать для доступа к объектной модели ведущего приложения и доступа к другим функциям, доступным для надстроек VSTO. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Все созданные классы в проектах Office содержат обработчики событий `Startup` и `Shutdown` . Чтобы начать процесс написания кода, обычно код добавляется в эти обработчики событий. Для инициализации надстройки VSTO можно добавить код в обработчик событий `Startup` . Чтобы очистить ресурсы, используемые надстройкой VSTO, можно добавить код в обработчик событий `Shutdown` . Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Доступ к созданным классам во время выполнения
 При загрузке решения Office среда [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает экземпляры всех созданных классов в проекте. Для доступа к этим объектам из любого кода в вашем проекте можно использовать класс `Globals` . Например, класс можно использовать `Globals` для вызова кода в `ThisAddIn` классе из обработчика событий кнопки на ленте в надстройке VSTO.

 Дополнительные сведения см. [в разделе Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Рекомендации по пространству имен в решениях Office
 После создания проекта *пространство имен по умолчанию* (или *корневое пространство имен* в Visual Basic) проекта Office изменить будет нельзя. Пространство имен по умолчанию будет всегда соответствовать имени проекта, указанному при создании проекта. Если проект переименовать, пространство имен по умолчанию изменено не будет. Дополнительные сведения о пространстве имен по умолчанию в проектах см. в разделе [Страница приложения, конструктор проектов &#40;&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) и [Страница приложения в конструкторе проектов &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Изменение пространства имен классов ведущих элементов в проектах C#
 В проектах Office на Visual C# классы ведущих элементов (например, `ThisAddIn`, `ThisWorkbook`или `ThisDocument` ) имеют собственные пространства имен. По умолчанию пространство имен для ведущих элементов в проекте совпадает с именем проекта, которое было указано при создании проекта.

 Чтобы изменить пространство имен ведущих элементов в проекте Office на Visual C#, используйте свойство **Пространство имен для элемента узла** . Дополнительные сведения см. [в разделе Свойства в проектах Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Поддерживаемые языки программирования в проектах Office
 Шаблоны проектов Office в Visual Studio поддерживает только языки программирования Visual Basic и Visual C#. Поэтому эти шаблоны проектов доступны только в узлах **Visual Basic** и **Visual C#** в диалоговом окне **Создание проекта** в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Языковой вариант и программирование для Office
 Microsoft Office и Visual Basic для приложений (VBA) были разработаны для совместной работы с целью оптимизации рабочего процесса настройки приложения. Язык Visual Basic унаследовал некоторые результаты этих разработок. Например, Visual Basic поддерживает необязательные параметры. Это означает, что по сравнению с языком Visual C#, вы можете написать меньше кода при вызове некоторых методов в основных сборках взаимодействия Microsoft Office.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Программирование с помощью Visual Basic и Visual C# в решениях Office
 Решения Office можно создавать с помощью языков Visual Basic или Visual C#. Так как объектные модели Microsoft Office были разработаны для использования с Microsoft Visual Basic для приложений (VBA), разработчики Visual Basic могут комфортно работать с объектами, предоставляемыми приложениями Microsoft Office. Разработчики Visual C# могут использовать большинство тех же функций, что и разработчики Visual Basic. Но в некоторых случаях для использования объектной модели Office им необходимо написать дополнительный код. Основы процедур программирования при разработке решений Office и написание управляемого кода на Visual Basic и C# немного отличаются.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Основные различия между Visual Basic и Visual C #
<!-- markdownlint-enable MD003 MD020 -->

В следующей таблице показаны основные различия между Visual Basic и Visual C# при разработке решений Office.

|Функция|Описание|Поддержка Visual Basic|Поддержка Visual C#|
|-------------|-----------------|--------------------------|------------------------|
|Необязательные параметры|Многие методы Microsoft Office имеют параметры, которые не являются обязательными при вызове метода. Если для параметра никакое значение не передается, используется значение по умолчанию.|Visual Basic поддерживает необязательные параметры.|Visual C# поддерживает необязательные параметры в большинстве случаев. Дополнительные сведения см. [в разделе необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md).|
|Передача параметров по ссылке|В большинстве основных сборок взаимодействия Microsoft Office необязательные параметры могут передаваться по значению. Однако в некоторых основных сборках взаимодействия необязательные параметры, которые принимают ссылочные типы, должны передаваться по ссылке.<br /><br /> Дополнительные сведения о параметрах типа Value и Reference см. в статьях [Передача аргументов по значению и по ссылке &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (для Visual Basic) и [Передача параметров &#40;&#35; руководство по программированию с ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)&#41;.|Для передачи параметров по ссылке дополнительные действия не требуются. При необходимости компилятор Visual Basic автоматически передает параметры по ссылке.|В большинстве случаев компилятор Visual C# автоматически передает параметры по ссылке. Дополнительные сведения см. [в разделе необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md).|
|Параметризованные свойства|Некоторые свойства принимают параметры и действуют как функции только для чтения.|Visual Basic поддерживает свойства, принимающие параметры.|Visual C# поддерживаются свойства, принимающие параметры.|
|Позднее связывание|Позднее связывание подразумевает определение свойств объектов во время выполнения, а не приведение переменных к типу объекта во время разработки.|Visual Basic выполняет позднее связывание, если параметр **Option Strict** отключен. Если параметр **Option Strict** включен, для доступа к членам с поздним связыванием необходимо явным образом преобразовать объекты и использовать типы в пространстве имен <xref:System.Reflection> . Дополнительные сведения см. [в статье позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).|Visual C# выполняет позднее связывание в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Дополнительные сведения см. [в статье позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Основные различия между разработкой приложений Office и управляемым кодом
 В таблице ниже указаны основные различия между разработкой для Office и управляемым кодом, написанным на Visual Basic или Visual C#.

|Функция|Описание|Поддержка Visual Basic и Visual C#|
|-------------|-----------------|-----------------------------------------|
|Индексы массивов|Нижняя граница массива коллекций в приложениях Microsoft Office начинается с 1. Visual Basic и Visual C# используют массивы, которые начинаются с нуля. Дополнительные сведения см. в разделе [arrays &#40;C&#35; Guide программирование&#41;](/dotnet/csharp/programming-guide/arrays/index) и [массивы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Для доступа к первому элементу коллекции в объектной модели приложения Microsoft Office используйте индекс 1 вместо 0.|

## <a name="see-also"></a>См. также раздел

- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [События в проектах Office](../vsto/events-in-office-projects.md)
- [Пошаговое руководство. Назначение приложений Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)
- [Совместная разработка решений Office](../vsto/collaborative-development-of-office-solutions.md)

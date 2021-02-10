---
title: Объединение настроек VBA и параметров на уровне документа
description: Узнайте, как можно использовать код Visual Basic для приложений (VBA) в документе, который является частью настройки уровня документа для Microsoft Office Word или Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1c5f66042dad7051c856aa6158ea0a666a81e9b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938529"
---
# <a name="combine-vba-and-document-level-customizations"></a>Объединение настроек VBA и параметров на уровне документа
  Код Visual Basic для приложений (VBA) можно использовать в документе, который является частью настройки на уровне документа для Microsoft Office Word или Microsoft Office Excel. Код VBA можно вызывать в документе из сборки настройки, или проект можно настроить таким образом, чтобы позволить коду VBA в документе вызывать код в сборке настройки.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Поведение кода VBA в настройке уровня документа
 При открытии проекта в Visual Studio документ открывается в режиме конструктора. Код VBA не выполняется, если документ находится в режиме конструктора, поэтому можно работать над документом и кодом без выполнения кода VBA.

 При запуске решения обработчики событий в VBA и сборке настройки получают события, возникающие в документе, и выполняются оба набора кода. Заранее невозможно определить, какой из кодов будет выполнен раньше. Это необходимо определить путем тестирования в каждом конкретном случае. Если два набора кода тщательно не скоординированы и не протестированы, можно получить неожиданные результаты.

## <a name="call-vba-code-from-the-customization-assembly"></a>Вызов кода VBA из сборки настройки
 В документах Word можно вызывать макросы, а в книгах Excel — функции и макросы. Для этого используйте один из следующих методов:

- Для Word вызовите <xref:Microsoft.Office.Interop.Word._Application.Run%2A> метод <xref:Microsoft.Office.Interop.Word.Application> класса.

- Для Excel необходимо вызвать метод <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> класса <xref:Microsoft.Office.Interop.Excel.Application> .

  Для каждого метода первый параметр определяет имя макроса или функции, которую необходимо вызвать, а оставшиеся необязательные параметры указывают параметры, передаваемые в макрос или функцию. Первый параметр может иметь различные форматы для Word и Excel:

- Для Word первый параметр является строкой, которая может быть любой комбинацией из имен шаблона, модуля и макроса. Если указать имя документа, код сможет выполнять макросы только в документах, относящихся к текущему контексту, а не любые макросы в любом документе.

- Для Excel первый параметр может быть строкой, которая указывает имя макроса, объектом <xref:Microsoft.Office.Interop.Excel.Range> , указывающим, где находится функция, или идентификатором регистра для зарегистрированной функции DLL (XLL). Если передается строка, она строка будет оцениваться в контексте активного листа.

  В следующем примере кода показано, как вызвать макрос с именем `MyMacro` из проекта на уровне документа для Excel. В этом примере предполагается, что `MyMacro` определен в `Sheet1`.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Сведения об использовании глобальной `missing` переменной вместо необязательных параметров в Visual C# см. в разделе [написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Вызов кода в настройках уровня документа из VBA
 Проект на уровне документа для Word или Excel можно настроить таким образом, чтобы код Visual Basic для приложений (VBA) в документе мог вызывать код в сборке настройки. Это полезно в следующих случаях:

- Необходимо расширить существующий код VBA в документе с помощью функций в настройке на уровне документа, которая связана с тем же документом.

- Службы, разрабатываемые в настройке на уровне документа, необходимо сделать доступными для конечных пользователей, которые могут получать доступ к этим службам, путем написания кода VBA в документе.

  Средства разработки Office в Visual Studio предоставляют аналогичную функцию для надстроек VSTO. При разработке надстройки VSTO можно вызывать код в надстройке VSTO из других Microsoft Office решений. Дополнительные сведения см. [в разделе вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Эту функцию нельзя использовать в проектах шаблонов Word. Ее можно использовать только в проектах документов Word, книг Excel или шаблонов Excel.

## <a name="requirements"></a>Требования
 Перед обеспечением для кода VBA возможности вызывать сборку настройки убедитесь, что проект соответствует следующим требованиям:

- Документ должен иметь одно из следующих расширений имени файла:

  - Для Word: *. docm* или *. doc*

  - Для Excel: *. xlsm*, *. xltm*, *. xls* или *. xlt*

- Документ должен уже содержать проект VBA, который содержит в себе код VBA.

- Для кода VBA в документе должна существовать возможность работы без вывода запросов пользователю на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.

- Проект Office должен содержать по крайней мере один общий класс с одним или несколькими общими членами, которые вы предоставляете коду VBA.

     Коду VBA можно предоставлять методы, свойства и события. Предоставляемым классом может быть класс ведущего элемента (например, `ThisDocument` для Word или `ThisWorkbook` и `Sheet1` для Excel) или другой класс, определенный в проекте. Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Включение кода VBA для вызова сборки настройки
 Для предоставления членов в сборке настройки коду VBA в документе можно использовать два способа:

- В код VBA можно предоставлять члены класса ведущего элемента в проекте [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . Для этого установите для свойства **EnableVbaCallers** ведущего элемента значение **True** в окне **Свойства** , когда ведущий элемент (то есть, документ, лист или книга) открыт в конструкторе. Visual Studio автоматически выполнит все необходимые действия, чтобы код VBA мог вызывать члены класса.

- В код VBA можно предоставлять члены любого общего класса в проекте Visual C# или члены класса элемента, не являющегося ведущим, в проекте [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . Этот параметр расширяет возможность выбора классов, которые можно предоставить коду VBA, но это также потребует выполнения дополнительных действий вручную.

   Для этого необходимо выполнить следующие основные шаги:

  1. Предоставьте класс для COM.

  2. Переопределите метод **GetAutomationObject** класса ведущего элемента в своем проекте для возврата экземпляра класса, который вы предоставляете коду VBA.

  3. Для свойства **ReferenceAssemblyFromVbaProject** любого класса ведущего элемента в проекте установите значение **True**. Это внедряет библиотеку типов сборки настройки в саму сборку и добавляет ссылку на библиотеку типов в проект VBA в документе.

  Подробные инструкции см. в разделе [руководство. предоставление кода коду VBA в Visual Basic проекте](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) и [инструкции: предоставление кода VBA в проекте Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  Свойства **EnableVbaCallers** и **ReferenceAssemblyFromVbaProject** доступны в окне **Свойства** только во время разработки. Они не могут использоваться во время выполнения. Для просмотра свойств откройте конструктор для ведущего элемента в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения о конкретных задачах, выполняемых Visual Studio при задании этих свойств, см. [в разделе задачи, выполняемые свойствами ведущего элемента](#PropertyTasks).

> [!NOTE]
> Если книга или документ еще не содержит кода VBA, или код VBA в документе не является доверенным для выполнения, при установке для свойства **EnableVbaCallers** или **ReferenceAssemblyFromVbaProject** значения **True** вы получите сообщение об ошибке. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Использование элементов в коде VBA для вызова сборки настройки
 После настройки своего проекта для обеспечения для кода VBA возможности вызывать сборку настройки Visual Studio добавляет в проект VBA в документе следующие члены:

- Для всех проектов Visual Studio добавляет глобальный метод с именем `GetManagedClass`.

- Для [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] проектов, в которых предоставляются члены класса ведущего элемента с помощью свойства **свойства EnableVbaCallers** , Visual Studio также добавляет свойство с именем в `CallVSTOAssembly` `ThisDocument` модуль,, `ThisWorkbook` `Sheet1` , `Sheet2` или `Sheet3` в проект VBA.

  Для доступа к открытым членам класса, который вы предоставляете коду VBA в проекте, можно использовать свойство `CallVSTOAssembly` или метод `GetManagedClass` .

> [!NOTE]
> Во время разработки и развертывания решения существуют несколько различных копий документа, в которые можно добавить код VBA. Дополнительные сведения см. в разделе [рекомендации по добавлению кода VBA в документ](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Использование свойства Каллвстоассембли в проекте Visual Basic
 Для доступа к открытым членам, которые вы добавили в класс ведущего элемента, используйте свойство `CallVSTOAssembly` . Например, следующий макрос VBA вызывает метод с именем `MyVSTOMethod` , который определен в классе `Sheet1` в проекте книги Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Это свойство является более удобным способом вызова сборки настройки, чем использование метода `GetManagedClass` напрямую. `CallVSTOAssembly` возвращает объект, представляющий класс ведущего элемента, который вы предоставили коду VBA. Члены и параметры метода возвращенного объекта отображаются в IntelliSense.

 Свойство `CallVSTOAssembly` имеет объявление, похожее на следующий код. Данный код предполагает, что вы предоставили коду VBA класс ведущего элемента `Sheet1` в проекте книги Excel с именем `ExcelWorkbook1` .

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Использование метода Жетманажедкласс
 Чтобы использовать глобальный метод `GetManagedClass` , передайте объект VBA, соответствующий классу ведущего элемента, который содержит переопределенный метод **GetAutomationObject** . Затем для доступа к классу, который вы предоставляете коду VBA, используйте возвращенный объект.

 Например, следующий макрос VBA вызывает метод с именем `MyVSTOMethod` , который определен в классе ведущего элемента `Sheet1` в проекте книги Excel с именем `ExcelWorkbook1`.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 Метод `GetManagedClass` имеет следующее объявление:

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Этот метод возвращает объект, представляющий класс, который вы предоставили коду VBA. Члены и параметры метода возвращенного объекта отображаются в IntelliSense.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Рекомендации по добавлению кода VBA в документ
 Существует несколько различных копий документа, где можно добавлять код VBA, который вызывает настройку на уровне документа.

 В ходе разработки и тестирования решения можно писать код VBA в документе, который открывается при отладке или запуске проекта в Visual Studio (то есть, документе в выходной папке сборки). Тем не менее, любой код VBA, добавляемый в этот документ, будут перезаписан в следующий раз при сборке проекта, так как Visual Studio заменяет документ в выходной папке сборки копией документа из главной папки проекта.

 Если необходимо сохранить код VBA, добавляемый в документ при отладке или выполнении решения, скопируйте код VBA в документ в папке проекта. Дополнительные сведения о процессе сборки см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

 Когда вы готовы к развертыванию решения, существует три основных расположения документа, куда можно добавлять код VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>В папке проекта на компьютере разработчика
 Это расположение удобно, если вы полностью контролируете код VBA в документе и код настройки. Так как документ находится на компьютере разработчика, вы можете легко изменять код VBA при изменении кода настройки. Код VBA, добавляемый в эту копию документа, остается в документе в ходе сборки, отладки и публикации решения.

 Если документ открыт в конструкторе, то добавлять код VBA в него нельзя. Сначала необходимо закрыть документ в конструкторе, а затем открыть его непосредственно в Word или Excel.

> [!CAUTION]
> При добавлении кода VBA, который выполняется при открытии документа, иногда этот код может повредить документ или сделать невозможным его открытие в конструкторе.

### <a name="in-the-publish-or-installation-folder"></a>В папке публикации или установки
 В некоторых случаях может быть необходимо добавление кода VBA в документ в папке публикации или папке установки. Например, этот вариант можно выбрать, если код VBA создан и протестирован другим разработчиком на компьютере, на котором Visual Studio не установлен.

 Если пользователи устанавливают решение непосредственно из папки публикации, код VBA необходимо добавлять в документ при каждой публикации решения. Visual Studio перезаписывает документ в папке публикации в ходе публикации решения.

 Если пользователи устанавливают решение из папки установки, отличной от папки публикации, то добавления кода VBA в документ при каждой публикации решения можно избежать. Если обновление публикации готово для перемещения из папки публикации в папку установки, скопируйте все файлы в папку установки, кроме самого документа.

### <a name="on-the-end-user-computer"></a>На компьютере конечного пользователя
 Если конечные пользователи являются разработчиками VBA, вызывающими службы, которые вы указываете в настройке на уровне документа, им можно сообщить способ вызова кода с помощью свойства `CallVSTOAssembly` или метода `GetManagedClass` в их копиях документа. При публикации обновлений в решении код VBA в документе на компьютере конечного пользователя не перезаписывается, поскольку документ не изменяется при публикации обновлений.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Задачи, выполняемые свойствами ведущего элемента
 Когда вы используете свойства **EnableVbaCallers** и **ReferenceAssemblyFromVbaProject** , Visual Studio выполняет различные наборы задач.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Если для свойства **EnableVbaCallers** ведущего элемента установить значение **True** в проекте Visual Basic, то Visual Studio выполняет следующие задачи:

1. Добавляет атрибуты <xref:Microsoft.VisualBasic.ComClassAttribute> и <xref:System.Runtime.InteropServices.ComVisibleAttribute> в класс ведущего элемента.

2. Переопределяет метод **GetAutomationObject** класса ведущего элемента.

3. Устанавливает для свойства **ReferenceAssemblyFromVbaProject** ведущего элемента значение **True**.

   Если для свойства **EnableVbaCallers** снова установить значение **False**, Visual Studio выполняет следующие задачи:

4. Удаляет атрибуты <xref:Microsoft.VisualBasic.ComClassAttribute> и <xref:System.Runtime.InteropServices.ComVisibleAttribute> из класса `ThisDocument` .

5. Удаляет метод **GetAutomationObject** из класса ведущего элемента.

   > [!NOTE]
   > Visual Studio не задает автоматически для свойства **ReferenceAssemblyFromVbaProject** значение **False**. Для этого свойства значение **False** можно установить вручную с помощью окна **Свойства** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Если для свойства **ReferenceAssemblyFromVbaProject** любого ведущего элемента в проекте Visual Basic или Visual C# установлено значение **True**, Visual Studio выполняет следующие задачи:

1. Создает библиотеку типов для сборки настройки и внедряет библиотеку типов в сборку.

2. Добавляет ссылку на следующие библиотеки типов в проекте VBA в документе:

   - Библиотека типов для сборки настройки.

   - Инструменты Microsoft Visual Studio для библиотеки типов Office Execution Engine 9.0. Эта библиотека типов включена в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

   Если для свойства **ReferenceAssemblyFromVbaProject** снова установить значение **False**, Visual Studio выполняет следующие задачи:

3. Удаляет ссылки на библиотеку типов из проекта VBA в документе.

4. Удаляет внедренные библиотеки типов из сборки.

## <a name="troubleshoot"></a>Диагностика
 Ниже перечислены некоторые распространенные ошибки и предложения по их устранению.

|Ошибка|Предложение|
|-----------|----------------|
|После задания свойства **EnableVbaCallers** или **ReferenceAssemblyFromVbaProject** появляется сообщение об ошибке, указывающее, что документ не содержит проект VBA, или что у вас нет разрешения на доступ к проекту VBA в документе.|Убедитесь, что документ в проекте содержит по крайней мере один макрос VBA, что проекту VBA задан достаточный уровень доверия для выполнения, и что проект VBA не защищен с помощью пароля.|
|После задания свойства **EnableVbaCallers** или **ReferenceAssemblyFromVbaProject** появляется сообщение об ошибке, указывающее, что объявление <xref:System.Runtime.InteropServices.GuidAttribute> отсутствует или повреждено.|Убедитесь, что <xref:System.Runtime.InteropServices.GuidAttribute> объявление находится в файле *AssemblyInfo.CS* или *AssemblyInfo. vb* в проекте, и для этого атрибута задан допустимый идентификатор GUID.|
|После задания свойства **EnableVbaCallers** или **ReferenceAssemblyFromVbaProject** появляется сообщение об ошибке, указывающее, что номер версии, указанный в <xref:System.Reflection.AssemblyVersionAttribute> , не является допустимым.|Убедитесь, что в <xref:System.Reflection.AssemblyVersionAttribute> качестве объявления в файле *AssemblyInfo.CS* или *AssemblyInfo. vb* в проекте задан допустимый номер версии сборки. Сведения о номерах версий сборки см. в классе <xref:System.Reflection.AssemblyVersionAttribute> .|
|После переименования сборки настройки код VBA, вызывающий эту сборку, перестает работать.|Если изменить имя сборки настройки после его предоставления коду VBA, то связь между проектом VBA в документе и сборкой настройки будет нарушена. Чтобы устранить эту проблему, задайте для свойства **ReferenceFromVbaAssembly** в своем проекте значение **False** , а потом снова **True**, и замените все ссылки на старое имя сборки в коде VBA новым именем сборки.|

## <a name="see-also"></a>См. также раздел
- [Руководство. предоставление кода коду VBA в Visual Basicном проекте](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Руководство. предоставление кода VBA в проекте Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Пошаговое руководство. вызов кода из VBA в Visual Basicном проекте](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Пошаговое руководство. вызов кода из VBA в проекте Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Сравнение решений VBA и Office в Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)

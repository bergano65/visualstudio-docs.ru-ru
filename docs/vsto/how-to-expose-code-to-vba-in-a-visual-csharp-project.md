---
title: Практическое руководство. Предоставить доступ к коду, коду VBA в C# проекта
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac41f4da29b95ba1fcd1601f98104956d584212a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419524"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Практическое руководство. Предоставить доступ к коду, коду VBA в визуальном элементе C# проекта
  Вы можете предоставлять код в проект Visual C# в Visual Basic для приложений (VBA), если требуется два вида код для взаимодействия друг с другом.

 Процесс Visual C# отличается от процесса Visual Basic. Дополнительные сведения см. в разделе [Как Предоставить доступ к коду, коду VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Предоставить доступ к коду в проекте Visual C#
 Чтобы включить код VBA мог вызывать код в проекте Visual C#, измените код, чтобы он был видим для COM и задайте **ReferenceAssemblyFromVbaProject** свойства **True** в конструкторе.

 Пошаговое руководство, которое демонстрирует вызов метода в визуальном элементе C# проекта из VBA см [Пошаговое руководство: Вызов кода из VBA в Visual c#&#35; проекта](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Для предоставления кода в проекте Visual C# код VBA

1. Откройте или создайте проект уровня документа, который основан на документ, книгу Excel или шаблон Excel с поддержкой макросов и который уже содержит код VBA.

    Дополнительные сведения о форматах файлов документов, поддерживающих макросы, см. в разделе [объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Эту функцию нельзя использовать в проектах шаблонов Word.

2. Убедитесь, что код VBA в документе может выполняться без вывода запроса на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.

3. Добавьте элемент, который вы хотите предоставить коду VBA в открытый класс в проекте, и объявите новый элемент как **открытый**.

4. Примените следующий <xref:System.Runtime.InteropServices.ComVisibleAttribute> и <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибуты к классу, который вы предоставляете коду VBA. Эти атрибуты делают класс видимым для модели COM, но без создания интерфейса класса.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Переопределить **GetAutomationObject** метод из класса ведущего элемента в проекте для возврата экземпляра класса, который вы предоставляете коду VBA:

   - Если вы предоставляете коду VBA класс ведущего элемента, переопределить **GetAutomationObject** метод, который принадлежит к этому классу и возвращает текущий экземпляр класса.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Если класс, который не является элементом узла коду VBA, переопределить **GetAutomationObject** метод любого ведущего элемента проекта и возвращать экземпляр класса элемента, отличных от имени компьютера. Например, в следующем коде предполагается, что вы предоставляете класс с именем `DocumentUtilities` коду VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Дополнительные сведения о ведущих элементах см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

6. Извлечение интерфейса в классе, который вы предоставляете коду VBA. В **извлечение интерфейса** диалоговом окне выберите открытые элементы, которые требуется включить в объявлении интерфейса. Дополнительные сведения см. в разделе [интерфейс рефакторинг для извлечения](../ide/reference/extract-interface.md).

7. Добавить **открытый** ключевое слово объявление интерфейса.

8. Сделать интерфейс видимым для COM, добавив следующий <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Откройте документ (для Word) или лист (для Excel) в конструкторе в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

10. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.

    > [!NOTE]
    > Если книга или документ не содержит кода VBA, или если код VBA в документе не является доверенным для выполнения, вы получите сообщение об ошибке при установке **ReferenceAssemblyFromVbaProject** свойства **True**. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.

11. Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении VBA кода в книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], код VBA будут потеряны при очередном при сборке проекта. Это обусловлено папку перезаписывается каждый раз при сборке проекта выходной документ в сборке.

     На этом этапе Visual Studio настраивает проект, чтобы проект VBA можно вызывать сборку. Visual Studio также добавляет метод с именем `GetManagedClass` проект VBA. Этот метод можно вызвать из любого места в проекте VBA для доступа к классу, который вы предоставляете коду VBA.

12. Выполните построение проекта.

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Пошаговое руководство: Вызов кода из VBA в Visual c#&#35; проекта](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Практическое руководство. Предоставить доступ к коду, коду VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)

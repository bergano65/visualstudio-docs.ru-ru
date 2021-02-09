---
title: Руководство. предоставление кода коду VBA в Visual Basicном проекте
description: Сведения о том, как можно предоставить код в проекте Visual Basic для Visual Basic для приложений (VBA), если требуется, чтобы два типа кода взаимодействовал друг с другом.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913492"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Руководство. предоставление кода коду VBA в Visual Basicном проекте
  Можно предоставить код в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] проекте для Visual Basic для приложений кода (VBA), если требуется, чтобы два типа кода взаимодействовал друг с другом.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Процесс Visual Basic отличается от процесса Visual C#. Дополнительные сведения см. в разделе [руководство. предоставление кода VBA в проекте Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Процесс отличается для кода в классе ведущего элемента, чем для кода в других классах:

- [Предоставление кода в классе ведущего элемента](#HostItemCode)

- [Предоставить код, не наявляющийся классом ведущего элемента](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Предоставление кода в классе ведущего элемента
 Чтобы включить код VBA для вызова Visual Basic кода в классе ведущего элемента, задайте для свойства **свойства EnableVbaCallers** ведущего элемента **значение true**.

 Пошаговое руководство, в котором показано, как предоставить метод класса ведущего элемента и затем вызвать его из VBA, см. [в разделе Пошаговое руководство. вызов кода из VBA в Visual Basic проекте](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Предоставление кода в ведущем элементе для VBA

1. Откройте или создайте проект на уровне документа, [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] основанный на документе Word, книге Excel или шаблоне Excel, который поддерживает макросы и уже содержит код VBA.

     Дополнительные сведения о форматах файлов документов, поддерживающих макросы, см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Эту функцию нельзя использовать в проектах шаблонов Word.

2. Убедитесь, что код VBA в документе разрешен для выполнения без запроса на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.

3. Добавьте свойство, метод или событие, которые необходимо предоставить коду VBA, в один из классов ведущих элементов в проекте и объявите новый член как **открытый**. Имя класса зависит от приложения:

    - В проекте Word класс ведущего элемента по умолчанию имеет имя `ThisDocument` .

    - В проекте Excel классы ведущих элементов имеют имена `ThisWorkbook` ,, и по `Sheet1` `Sheet2` `Sheet3` умолчанию.

4. Задайте для свойства **свойства EnableVbaCallers** ведущего элемента **значение true**. Это свойство доступно в окне **Свойства** , когда ведущий элемент открыт в конструкторе.

     После установки этого свойства Visual Studio автоматически устанавливает для свойства **ReferenceAssemblyFromVbaProject** **значение true**.

    > [!NOTE]
    > Если книга или документ еще не содержат код VBA или если код VBA в документе не является доверенным для выполнения, то при установке свойства **свойства EnableVbaCallers** в **значение true** будет получено сообщение об ошибке. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.

5. Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении кода VBA в книгу или документ во время выполнения проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] среды код VBA будет потерян при следующей сборке проекта. Это обусловлено тем, что документ в выходной папке построения перезаписывается при каждом построении проекта.

     На этом этапе Visual Studio настраивает проект таким образом, чтобы проект VBA мог вызывать сборку. Visual Studio также добавляет свойство с именем в `CallVSTOAssembly` `ThisDocument` модуль, `ThisWorkbook` , `Sheet1` , `Sheet2` или `Sheet3` в проект VBA. Это свойство можно использовать для доступа к открытым членам класса, предоставленным VBA.

6. Выполните построение проекта.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Предоставить код, не наявляющийся классом ведущего элемента
 Чтобы включить код VBA для вызова Visual Basic кода, который не находится в классе ведущего элемента, измените код так, чтобы он был видим для VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Предоставление коду VBA кода, который не входит в класс ведущего элемента

1. Откройте или создайте проект на уровне документа, [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] основанный на документе Word, книге Excel или шаблоне Excel, который поддерживает макросы и уже содержит код VBA.

     Дополнительные сведения о форматах файлов документов, поддерживающих макросы, см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Эту функцию нельзя использовать в проектах шаблонов Word.

2. Убедитесь, что код VBA в документе разрешен для выполнения без запроса на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.

3. Добавьте член, который требуется предоставить коду VBA, в открытый класс в проекте и объявите новый член как **открытый**.

4. Примените следующие <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualBasic.ComClassAttribute> атрибуты и к классу, который предоставляется VBA. Эти атрибуты делают класс видимым для VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Переопределите метод **GetAutomationObject** класса ведущего элемента в своем проекте для возврата экземпляра класса, который вы предоставляете коду VBA. В следующем примере кода предполагается, что вы предоставляете в VBA класс с именем `DocumentUtilities` .

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Откройте документ (для Word) или лист (для Excel) в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.

    > [!NOTE]
    > Если книга или документ еще не содержат код VBA или если код VBA в документе не является доверенным для выполнения, то при установке свойства **ReferenceAssemblyFromVbaProject** в **значение true** будет получено сообщение об ошибке. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.

8. Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении кода VBA в книгу или документ во время выполнения проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] среды код VBA будет потерян при следующей сборке проекта. Это обусловлено тем, что документ в выходной папке построения перезаписывается при каждом построении проекта.

     На этом этапе Visual Studio настраивает проект таким образом, чтобы проект VBA мог вызывать сборку. Visual Studio также добавляет метод с именем `GetManagedClass` в проект VBA. Этот метод можно вызвать из любого места в проекте VBA для доступа к классу, предоставленному VBA.

9. Выполните построение проекта.

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Объединение настроек VBA и параметров на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Пошаговое руководство. вызов кода из VBA в Visual Basicном проекте](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Руководство. предоставление кода VBA в проекте Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)

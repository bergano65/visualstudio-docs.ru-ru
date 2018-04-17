---
title: 'Как: предоставлять к коду VBA в проекте Visual Basic | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39dc659f7c8841bcf350249332278091232a32d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>How to: Expose Code to VBA in a Visual Basic Project
  Код в может предоставить [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] проекта Visual Basic для приложений (VBA), если требуется два типа кода для взаимодействия друг с другом.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Процесс Visual Basic отличается от процесса Visual C#. Дополнительные сведения см. в разделе [как: предоставлять к коду VBA в Visual C&#35; проекта](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Процесс происходит отличается от кода в класс ведущего элемента для кода в других классах.  
  
-   [Предоставление доступа к коду в классе ведущего элемента](#HostItemCode)  
  
-   [Предоставление доступа к коду, который не находится в классе ведущего элемента](#NonHostItem)  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как сделать I: вызову кода VSTO из VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Предоставление доступа к коду в классе ведущего элемента  
 Чтобы код VBA мог вызывать код Visual Basic в класс ведущего элемента, установите **EnableVbaCallers** свойство ведущего элемента значение **True**.  
  
 Пошаговое руководство для предоставления метода класса ведущего элемента, а затем вызвать его из VBA см [Пошаговое руководство: вызов кода из VBA в проекте Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Дополнительные сведения о ведущих элементах см. в разделе [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Чтобы предоставить доступ к коду в ведущем элементе в код VBA  
  
1.  Откройте или создайте уровня документа [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] проекта, основанного на документе Word, книги Excel или шаблон Excel с поддержкой макросов и уже содержащем код VBA.  
  
     Дополнительные сведения о форматах файлов документов, поддерживающих макросы см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Эту функцию нельзя использовать в проектах шаблонов Word.  
  
2.  Убедитесь, что код VBA в документе разрешено работы без вывода запросов пользователю на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.  
  
3.  Добавьте свойство, метод или событие, которое вы хотите предоставить коду VBA в один из классов ведущих элементов в проекте, и объявите новый элемент как **открытый**. Имя класса зависит от приложения:  
  
    -   В слове проект, в класс ведущего элемента называется `ThisDocument` по умолчанию.  
  
    -   В проекте Excel с именем классов ведущих элементов `ThisWorkbook`, `Sheet1`, `Sheet2`, и `Sheet3` по умолчанию.  
  
4.  Задать **EnableVbaCallers** свойство для ведущего элемента значение **True**. Это свойство доступно в **свойства** окна, когда ведущий элемент открыт в конструкторе.  
  
     После установки этого свойства, Visual Studio автоматически задает **ReferenceAssemblyFromVbaProject** свойства **True**.  
  
    > [!NOTE]  
    >  Если книга или документ не содержит кода VBA, или если код VBA в документе не является доверенным для выполнения, вы получите сообщение об ошибке при установке **EnableVbaCallers** свойства **True**. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.  
  
5.  Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении кода VBA в книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], код VBA будут потеряны при очередном при построении проекта. Это потому, что документ в выходной папке сборки перезаписывается каждый раз при сборке проекта.  
  
     На этом этапе Visual Studio настраивает проект, чтобы проект VBA можно вызывать сборку. Visual Studio также добавляет свойство с именем `CallVSTOAssembly` для `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, или `Sheet3` в проекте VBA. Это свойство можно использовать для доступа к открытым членам класса, который был предоставлен коду VBA.  
  
6.  Выполните построение проекта.  
  
##  <a name="NonHostItem"></a> Предоставление доступа к коду, который не находится в классе ведущего элемента  
 Чтобы код VBA мог вызывать код Visual Basic, не в класс ведущего элемента, измените код, чтобы он видны для VBA.  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Чтобы предоставить код, который не находится в классе ведущего элемента в код VBA  
  
1.  Откройте или создайте уровня документа [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] проекта, основанного на документе Word, книги Excel или шаблон Excel с поддержкой макросов и уже содержащем код VBA.  
  
     Дополнительные сведения о форматах файлов документов, поддерживающих макросы см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Эту функцию нельзя использовать в проектах шаблонов Word.  
  
2.  Убедитесь, что код VBA в документе разрешено работы без вывода запросов пользователю на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.  
  
3.  Добавьте элемент, который вы хотите предоставить коду VBA в открытый класс проекта и объявите новый элемент как **открытый**.  
  
4.  Применить следующие <xref:System.Runtime.InteropServices.ComVisibleAttribute> и <xref:Microsoft.VisualBasic.ComClassAttribute> атрибуты к классу, который вы предоставляете коду VBA. Эти атрибуты делают класс видимым для VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Переопределите метод **GetAutomationObject** класса ведущего элемента в своем проекте для возврата экземпляра класса, который вы предоставляете коду VBA. В следующем примере кода предполагается, что вы предоставляете класс с именем `DocumentUtilities` коду VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Откройте документ (для Word) или рабочий лист (для Excel) конструктор в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.  
  
    > [!NOTE]  
    >  Если книга или документ не содержит кода VBA, или если код VBA в документе не является доверенным для выполнения, вы получите сообщение об ошибке при установке **ReferenceAssemblyFromVbaProject** свойства **значение True** . Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.  
  
8.  Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении кода VBA в книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], код VBA будут потеряны при очередном при построении проекта. Это потому, что документ в выходной папке сборки перезаписывается каждый раз при сборке проекта.  
  
     На этом этапе Visual Studio настраивает проект, чтобы проект VBA можно вызывать сборку. Visual Studio также добавляет метод с именем `GetManagedClass` в проект VBA. Этот метод можно вызывать из любого места в проекте VBA для доступа к классу, который был предоставлен коду VBA.  
  
9. Выполните построение проекта.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)   
 [Пошаговое руководство: Вызов кода из VBA в проекте Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Как: предоставлять к коду VBA в Visual C&#35; проекта](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  
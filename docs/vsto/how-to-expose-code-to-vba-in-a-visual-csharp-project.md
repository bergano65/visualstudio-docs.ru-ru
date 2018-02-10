---
title: "Как: предоставлять к коду VBA в проекте Visual C# | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 1b750137a52d30688f69c825f83f72c7cbeebe45
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual C#
  Код Visual C# проекта на Visual Basic для приложений (VBA) можно предоставлять, если требуется два типа кода для взаимодействия друг с другом.  
  
 Процесс Visual C# отличается от процесса Visual Basic. Дополнительные сведения см. в разделе [как: предоставлять к коду VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Предоставление доступа к коду в проекте Visual C#  
 Чтобы позволить коду VBA для вызова кода в проекте Visual C#, измените код, чтобы его видимым для COM и задайте **ReferenceAssemblyFromVbaProject** свойства **True** в конструкторе.  
  
 Пошаговое руководство для вызова метода в проекте Visual C# из VBA см [Пошаговое руководство: вызов кода из VBA в Visual C &#35; Проект](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Чтобы предоставить доступ к коду в проекте Visual C# в код VBA  
  
1.  Откройте или создайте проект уровня документа, основанного на документе Word, книги Excel или шаблон Excel с поддержкой макросов и уже, содержащей код VBA.  
  
     Дополнительные сведения о форматах файлов документов, поддерживающих макросы см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Эту функцию нельзя использовать в проектах шаблонов Word.  
  
2.  Убедитесь, что код VBA в документе разрешено работы без вывода запросов пользователю на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.  
  
3.  Добавьте элемент, который вы хотите предоставить коду VBA в открытый класс проекта и объявите новый элемент как **открытый**.  
  
4.  Применить следующие <xref:System.Runtime.InteropServices.ComVisibleAttribute> и <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибуты к классу, который вы предоставляете коду VBA. Эти атрибуты делают класс видимым для модели COM, но без создания интерфейса класса.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Переопределить **GetAutomationObject** метод из класса ведущего элемента в проекте для возврата экземпляра класса, который вы предоставляете коду VBA:  
  
    -   Если вы предоставляете коду VBA класс ведущего элемента, следует переопределить **GetAutomationObject** метод принадлежит к этому классу, который возвращает текущий экземпляр класса.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Если вы предоставляете класс, который не является элементом узла в код VBA, переопределите **GetAutomationObject** метод любого ведущего элемента в проекте и возврата экземпляра класса элемента, не являющегося ведущим. Например, в следующем коде предполагается, что вы предоставляете класс с именем `DocumentUtilities` коду VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Дополнительные сведения о ведущих элементах см. в разделе [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Извлечение интерфейса от класса, который вы предоставляете коду VBA. В **извлечение интерфейса** диалогового окна выберите открытые элементы, которые требуется включить в объявлении интерфейса. Дополнительные сведения см. в разделе [извлечь рефакторинг интерфейса](../ide/reference/extract-interface.md).
  
7.  Добавить **открытый** ключевое слово объявление интерфейса.  
  
8.  Сделать интерфейс видимым для COM, добавив следующий код <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибута к интерфейсу.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Откройте документ (для Word) или рабочий лист (для Excel) в конструкторе в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.  
  
    > [!NOTE]  
    >  Если книга или документ не содержит кода VBA, или если код VBA в документе не является доверенным для выполнения, вы получите сообщение об ошибке при установке **ReferenceAssemblyFromVbaProject** свойства **True**. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.  
  
11. Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении VBA кода в книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], код VBA будут потеряны в следующий раз при построении проекта. Это так, как документ в построении выходной папки перезаписывается при каждом построении проекта.  
  
     На этом этапе Visual Studio настраивает проект, чтобы проект VBA можно вызывать сборку. Visual Studio также добавляет метод с именем `GetManagedClass` в проект VBA. Этот метод можно вызывать из любого места в проекте VBA для доступа к классу, который был предоставлен коду VBA.  
  
12. Выполните построение проекта.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Пошаговое руководство: Вызов кода из VBA в Visual C &#35; Проект](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
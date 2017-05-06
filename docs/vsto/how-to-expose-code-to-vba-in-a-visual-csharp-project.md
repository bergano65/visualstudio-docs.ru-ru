---
title: "Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual C#"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "настройки уровня документа [разработка решений Office в Visual Studio], предоставление доступа к коду"
  - "предоставление доступа к коду VBA"
  - "VBA [разработка решений Office в Visual Studio], предоставление доступа к коду (настройки уровня документа)"
  - "Visual C# [разработка решений Office в Visual Studio], предоставление доступа к коду VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual C# #
  В проекте Visual C\# можно предоставить доступ к коду со стороны кода VBA, если необходимо обеспечить взаимодействие двух типов кода.  
  
 Процесс Visual C\# отличается от процесса Visual Basic.  Дополнительные сведения см. в разделе [Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Предоставление доступа к коду в проекте Visual C\#  
 Чтобы предоставить коду VBA возможность обращаться к коду проекта Visual C\#, необходимо изменить код так, чтобы он стал видимым для COM, а затем в конструкторе присвоить свойству **ReferenceAssemblyFromVbaProject** значение **True**.  
  
 В разделе [Пошаговое руководство. Вызов кода из VBA в проекте Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md) представлены инструкции, демонстрирующие способ вызова метода в проекте Visual C\# из VBA.  
  
#### Предоставление доступа к коду в проекте Visual C\# со стороны VBA  
  
1.  Откройте или создайте проект уровня документа, основанный на документе Word, рабочей книге Excel или шаблоне Excel, поддерживающем макросы и уже содержащем код VBA.  
  
     Дополнительные сведения о форматах файлов документов, поддерживающих макросы, см. в разделе [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Эту функцию нельзя использовать в проектах шаблонов Word.  
  
2.  Убедитесь в том, что выполнение кода VBA в документе разрешено без вывода пользователю сообщения о необходимости включения макросов.  Чтобы сделать код VBA надежным и разрешить его выполнение, добавьте расположение проекта Office в список надежных расположений в параметрах центра управления безопасностью для Word или Excel.  
  
3.  Добавьте элемент, доступ к которому необходимо открыть для VBA, в открытый класс проекта и объявите новый элемент как **public**.  
  
4.  Примените атрибуты <xref:System.Runtime.InteropServices.ComVisibleAttribute> и <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> к классу, доступ к которому открывается для VBA.  Эти атрибуты делают класс видимым для COM без создания интерфейса класса:  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Переопределите метод **GetAutomationObject** класса ведущего элемента проекта, чтобы получить экземпляр класса, доступ к которому предоставляется VBA.  
  
    -   Если VBA предоставляется доступ к классу ведущего элемента, следует переопределить метод **GetAutomationObject**, принадлежащий данному классу, и получить текущий экземпляр класса:  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Если VBA предоставляется доступ к классу, не являющемуся ведущим элементом, следует переопределить метод **GetAutomationObject** любого ведущего элемента проекта и получить экземпляр класса элемента, не являющегося ведущим.  Например, следующий образец предполагает, что VBA предоставляется доступ к классу `DocumentUtilities`:  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Извлеките интерфейс из класса, доступ к которому предоставляется VBA.  В диалоговом окне **Извлечение интерфейса** выберите открытые элементы, которые необходимо включить в объявление интерфейса.  Дополнительные сведения см. в разделе [Рефакторинг для извлечения интерфейса &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md).  
  
7.  Добавьте в объявление интерфейса ключевое слово **public**.  
  
8.  Сделайте интерфейс видимым для COM, добавив следующий атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> в интерфейс:  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Откройте документ \(для Word\) или рабочий лист \(для Excel\) в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и измените его значение на **True**.  
  
    > [!NOTE]  
    >  Если рабочая книга или документ не содержат кода VBA, или если код VBA в документе не имеет доверия для выполнения, при присвоении свойству **ReferenceAssemblyFromVbaProject** значения **True** будет выдано сообщение об ошибке.  Это связано с тем, что в данном случае в Visual Studio не поддерживается изменение проекта VBA в документе.  
  
11. В появившимся окне с сообщением нажмите кнопку **ОК**.  Это сообщение служит для напоминания о том, что если код VBA добавляется в рабочую книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], то он будет утерян при следующем построении проекта.  Это происходит потому, что документ в выходной папке сборки перезаписывается каждый раз при построении проекта.  
  
     На этом этапе Visual Studio настраивает проект, чтобы проект VBA мог обращаться к данной сборке.  Visual Studio также добавляет метод с названием `GetManagedClass` в проект VBA.  Этот метод можно вызывать в любом месте проекта VBA для доступа к классу, открытому для VBA.  
  
12. Выполните построение проекта.  
  
## См. также  
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)   
 [Пошаговое руководство. Вызов кода из VBA в проекте Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Практическое руководство. Предоставление доступа к коду со стороны VBA в проекте Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
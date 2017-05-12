---
title: "События в проектах Office"
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
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], события"
  - "обработчики событий [разработка решений Office в Visual Studio]"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "настройки уровня документа [разработка решений Office в Visual Studio], события"
  - "Sheet2_Shutdown"
  - "Startup - событие"
  - "Sheet3_Shutdown"
  - "надстройки [разработка решений Office в Visual Studio], события"
  - "Shutdown - событие"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup - метод [разработка решений Office в Visual Studio]"
  - "Shutdown - метод [разработка решений Office в Visual Studio]"
  - "Sheet1_Shutdown"
  - "события [разработка решений Office в Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# События в проектах Office
  Каждый шаблон проекта Office автоматически создает несколько обработчиков событий. Обработчики событий для настроек на уровне документа несколько отличаются от обработчиков событий для надстроек VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Проекты уровня документа  
 Visual Studio предоставляет сформированный код для новых или существующих документов или листов в настройках на уровне документа. Этот код создает два различных события: **Startup** и **Shutdown**.  
  
### Событие запуска  
 Событие **Startup** возникает для каждого ведущего элемента \(документа, книги или листа\) после запуска документа и всех кодов инициализации в сборке. Это самая последняя операция, запускаемая в конструкторе класса, в котором выполняется ваш код. Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 При создании проекта на уровне документа Visual Studio создает обработчики событий для события **Startup** в созданных файлах кода:  
  
-   Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Startup`.  
  
-   Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### Событие завершения работы  
 Событие  **Shutdown**  возникает для каждого ведущего элемента \(документа или листа\), когда домен приложения, в который загружен ваш код, готов к выгрузке. Это самая последняя операция, которая должна быть вызвана в классе при выгрузке.  
  
 При создании проекта на уровне документа Visual Studio создает обработчики событий для события  **Shutdown**  в созданных файлах кода:  
  
-   Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Shutdown`.  
  
-   Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Не удаляйте программным образом элементы управления во время работы обработчика событий **Shutdown** документа. Если возникает событие **Shutdown**, элементы пользовательского интерфейса документа становятся недоступными. Если элементы управления необходимо удалить до закрытия приложения, добавьте свой код в другой обработчик событий, например, **BeforeClose** или **BeforeSave**.  
  
### Объявления метода обработчика событий  
 В каждое объявление метода обработчика событий передаются одни и те же аргументы: *sender* и *e*. В Excel аргумент *sender* ссылается на лист, например, `Sheet1` или `Sheet2`. В Microsoft Word аргумент *sender* ссылается на документ. Аргумент *e* ссылается на стандартные аргументы для события, которые не используются в этом случае.  
  
 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#121](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#121)]
 [!code-vb[Trin_VstcoreWordAutomation#121](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#121)]  
  
 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Excel.  
  
> [!NOTE]  
>  В следующем примере кода показаны обработчики событий в классе `Sheet1`. Имена обработчиков событий в других классах ведущих элементов соответствуют имени класса. Например, в классе `Sheet2` обработчик событий **Startup** имеет имя `Sheet2_Startup`. В классе `ThisWorkbook` обработчик событий **Startup** имеет имя `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#83)]  
  
### Порядок событий в проектах на уровне документа Excel  
 Обработчики **Startup** событий в проектах Excel вызываются в следующем порядке:  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Другие листы по порядку.  
  
 Обработчики событий  **Shutdown** в решении книги вызываются в следующем порядке:  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Другие листы по порядку.  
  
 Порядок определяется при компиляции проекта. Если пользователь изменяет порядок листов во время выполнения, это не приводит к изменению порядка, в котором появляются события при очередном открытии или закрытии книги.  
  
## Проекты надстроек VSTO  
 Visual Studio предоставляет сформированный код в надстройках VSTO. Этот код создает два различных события: <xref:Microsoft.Office.Tools.AddInBase.Startup> и <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### Событие запуска  
 Событие <xref:Microsoft.Office.Tools.AddIn.Startup> возникает после загрузки надстройки VSTO и запуска всего кода инициализации в сборке. Это событие обрабатывается методом `ThisAddIn_Startup` в файле сформированного кода.  
  
 Код в обработчике событий `ThisAddIn_Startup` — это первый код пользователя, подлежащий выполнению, если надстройка VSTO не переопределяет метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. В этом случае обработчик событий `ThisAddIn_Startup` вызывается после <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Не добавляйте код в обработчик событий `ThisAdd-In_Startup`, если для кода требуется открытый документа. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. Дополнительные сведения см. в разделе [Обращение к документу при запуске приложения Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Дополнительные сведения о последовательности запуска для надстроек VSTO см. в статье [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### Событие завершения работы  
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает, когда домен приложения, в котором загружен ваш код, готов к выгрузке. Это событие обрабатывается методом `ThisAddIn_Shutdown` в файле сформированного кода. Этот обработчик событий — последний код пользователя, выполняемый при выгрузке надстройки VSTO.  
  
#### Событие завершения работы в надстройках VSTO для Outlook  
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает только в том случае, когда пользователь отключает надстройку VSTO с помощью диалогового окна надстроек COM в Outlook. Оно не возникает при завершении работы Outlook. Если у вас есть код, который должен выполняться при завершении работы Outlook, обработайте одно из следующих событий:  
  
-   Событие <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> объекта <xref:Microsoft.Office.Interop.Outlook.Application>.  
  
-   Событие <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Explorer>.  
  
> [!NOTE]  
>  Чтобы Outlook принудительно создавал событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> при выходе, можно изменить реестр. Однако, если администратор отменяет эту настройку, любой код, добавленный в метод `ThisAddIn_Shutdown`, больше не будет выполняться при завершении работы Outlook. Дополнительные сведения см. в разделе [Изменения при завершении работы для Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
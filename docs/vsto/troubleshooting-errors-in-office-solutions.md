---
title: "Устранение неполадок в решениях Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords: troubleshooting [Office development in Visual Studio]
ms.assetid: 8bbf5433-1992-4ecf-ae1b-19117b8ebe43
caps.latest.revision: "69"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e74b2daab5d9a8f5840b9109edd871e311bc4cb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-errors-in-office-solutions"></a>Устранение ошибок в решениях Office
  Во время разработки решений Office в Visual Studio могут возникнуть проблемы при выполнении следующих задач:  
  
-   [Создание, обновление и открытие проектов](#creating)  
  
-   [Использование конструкторов](#designers)  
  
-   [Написание кода](#code)  
  
-   [Сборка проектов](#building)  
  
-   [Отладка проектов](#debugging)  
  
##  <a name="creating"></a>Создание, обновление и открытие проектов  
 При создании или открытии проектов Office могут возникнуть следующие ошибки.  
  
### <a name="the-project-cannot-be-created"></a>Невозможно создать проект  
 Произошла ошибка при попытке создать или открыть проект Office, но Visual Studio не имеет достаточно сведений, чтобы определить причину. Попробуйте закрыть проект, завершить работу и снова запустить Visual Studio.  
  
 Если вы пытаетесь создать проект уровня документа, возможно, что другой документ с тем же именем, что и документ в новом проекте, уже открыт в Excel или Word. Убедитесь, что все остальные экземпляры Excel или Word закрыты.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Свойства элемента управления теряются при создании нового проекта на основе документа из существующего проекта  
 При создании нового проекта Office, основанного на документе из существующего проекта, свойства элементов управления в документе не копируются в новый проект. Вам необходимо вручную сбросить свойства существующих элементов управления. Кроме того, можно сохранить свойства элементов управления, создав копию существующего проекта, а не создавая новый проект, или загрузив существующий проект в новое решение (в режиме конструктора) и скопировав и вставив элементы управления из существующего документа в новый документ.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Ошибки при создании проекта книги Excel на основе существующей книги  
 При создании нового проекта книги Excel на основе существующей книги могут возникнуть следующие ошибки.  
  
 В Excel: "Предупреждение о конфиденциальной информации: документ содержит макросы, элементы управления ActiveX, данные пакета расширения XML или веб-компоненты. Они могут включать личные сведения, которые нельзя удалить с помощью инспектора документов".  
  
 В Visual Studio: "Не удалось правильно загрузить конструктор".  
  
 Эти ошибки могут возникать при попытке создать проект, основанный на книге, из которой персональные данные были удалены с помощью инспектора документов. Чтобы избежать этой ошибки, выполните следующие действия перед созданием проекта.  
  
1.  Откройте книгу в Excel.  
  
2.  Откройте центр управления безопасностью в Excel.  
  
3.  На **параметры конфиденциальности** снять флажок **удалять личные сведения из свойств файла при сохранении** флажок.  
  
4.  Сохраните книгу и закройте Excel.  
  
### <a name="cannot-open-a-project-after-migration"></a>Не удается открыть проект после миграции  
 После переноса решения Office в Microsoft Office 2010 не удается открыть проект на компьютере разработки, где установлен только Microsoft Office 2007. Могут возникнуть следующие ошибки.  
  
 "Один или несколько проектов в решении были загружены неправильно. Дополнительную информацию см. в окне вывода".  
  
 "Не удается создать проект, поскольку приложение, связанное с этим типом проектов, не установлено на данном компьютере. Необходимо установить приложение Microsoft Office, связанное с этим типом проектов".  
  
 Чтобы устранить эту проблему, измените VBPROJ- или CSPROJ-файл. Для проекта Word замените HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" на HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Для проекта Excel замените HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" на HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}". Для проекта Outlook замените HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" на HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".  
  
 Или же убедитесь, что перенесенные проекты открываются только на компьютерах разработки с установленным Microsoft Office 2010.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Ошибки в обновленных проектах уровня документа Microsoft Office 2003, содержащих элементы управления Windows Forms  
 При обновлении проекта уровня документа Microsoft Office 2003, который содержит элементы управления Windows Forms, обновленный проект может вызывать ошибки компиляции или во время выполнения. Чтобы избежать этой проблемы, перед обновлением проекта установите второй выпуск среды выполнения набора средств Visual Studio 2005 для Office на компьютере разработки. Эта версия среды выполнения доступна в виде распространяемого пакета в Центре загрузки Майкрософт на странице [Среда выполнения набора средств Microsoft Visual Studio 2005 для Office (второй выпуск) (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 После завершения обновления проекта можно удалить среду выполнения набора средств Visual Studio 2005 для Office (второй выпуск) с компьютера разработчика, если она не используется другими решениями Office.  
  
##  <a name="designers"></a>Использование конструкторов  
 При работе с конструктором документов, книг или листов в проектах уровня документа могут возникнуть следующие ошибки.  
  
### <a name="designer-failed-to-load-correctly"></a>Не удалось правильно загрузить конструктор  
 Visual Studio не удается открыть конструктор в следующих случаях.  
  
-   Excel или Word уже открыты и отображают модальное диалоговое окно. Чтобы открыть конструктор, проверьте, открыто ли модальное диалоговое окно Excel или Word, и закройте все открытые модальные диалоговые окна. Если модальные диалоговые окна не открыты, возможно, требуются какие-либо другие действия для продолжения работы Excel или Word.  
  
-   В настоящее время выполняется отладка проекта. Чтобы открыть конструктор, остановите или завершите отладку.  
  
-   Надстройка VSTO для Excel, установленная на компьютере разработки, отображает диалоговое окно при запуске Excel. Чтобы создать проект уровня документа Excel, вначале необходимо отключить надстройку VSTO.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Элементы управления отображаются в виде черных прямоугольников в документе или листе  
 При группировке элементов управления в документе или листе Visual Studio больше не распознает их. Сгруппированных элементов управления не доступен в **свойства** окна и они отображаются в виде черных прямоугольников в документе или листе. Необходимо разгруппировать элементы управления, чтобы восстановить их работоспособность.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Элементы управления в шаблоне Word не видны в Visual Studio  
 При открытии шаблона Word в конструкторе Visual Studio элементы управления шаблона, расположенные не в тексте, могут не отображаться. Это, поскольку Visual Studio открывает шаблон Word в **обычный** представления. Чтобы просмотреть элементы управления, щелкните **представление** последовательно выберите пункты **вид Microsoft Office Word** и нажмите кнопку **разметки**.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>При вставке картинки из коллекции картинок в конструкторе Visual Studio не выполняется никаких действий  
 Если Excel или Word открыты в конструкторе Visual Studio, при нажатии **картинки** кнопку **иллюстрации** не удается открыть вкладку на ленте **картинки** области задач. Чтобы добавить картинку из коллекции картинок, необходимо открыть копию книги или документа в главной папке проекта (но не копию в папке \bin) вне Visual Studio, добавить картинки из коллекции картинок и сохранить книгу или документ.  
  
##  <a name="code"></a> Создание кода  
 При написании кода в проектах Office могут возникнуть следующие ошибки.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Некоторые события объектов Office недоступны при использовании C#  
 В некоторых случаях может появиться следующая ошибка компилятора при попытке получить доступ к определенному событию экземпляра типа основной сборки взаимодействия (PIA) Office в проекте Visual C#.  
  
 "Неоднозначность между "Microsoft.Office.Interop.Excel._Application.NewWorkbook" и "Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook"".  
  
 Эта ошибка означает, что вы пытаетесь получить доступ к событию, имя которого совпадает с именем другого свойства или метода объекта. Чтобы получить доступ к событию, необходимо привести объект к его *интерфейса события*.  
  
 Типы основных сборок взаимодействия Office с событиями реализуют два интерфейса: основной интерфейс со свойствами и методами и интерфейс событий, содержащий события, предоставляемые объектом. Этих интерфейсах событий используется соглашение об именовании *objectname*событий*n*_Event, например <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> и <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Если вам не удается получить доступ к событию, которое должно быть в объекте, приведите объект к типу соответствующего интерфейса событий.  
  
 Например, у объектов <xref:Microsoft.Office.Interop.Excel.Application> есть событие <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> и свойство <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>. Для обработки события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> приведите <xref:Microsoft.Office.Interop.Excel.Application> к интерфейсу <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>. В следующем примере кода показано, как сделать это в проекте уровня документа для Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Дополнительные сведения об интерфейсах событий в основных сборках взаимодействия Office см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>Не удается сослаться на классы основных сборок взаимодействия Office в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], по умолчанию код, ссылающийся на класс, определенный в основной сборке взаимодействия Office, не компилируется. Классы основных сборок взаимодействия используют соглашение об именовании *objectname*класса, такие как <xref:Microsoft.Office.Interop.Word.DocumentClass> и <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Так, следующий код из проекта надстройки VSTO для Word не будет компилироваться.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Этот код вызывает следующие ошибки компиляции.  
  
-   Visual Basic: «класс «DocumentClass» не разрешена ссылка при его сборка связана с использованием режима No-PIA.»  
  
-   Visual C#: «тип взаимодействия «Microsoft.Office.Interop.Word.DocumentClass» не может быть внедрен. Используйте подходящий интерфейс".  
  
 Чтобы устранить эту ошибку, измените код так, чтобы он ссылался на соответствующий интерфейс. Например, вместо того чтобы ссылаться на объект <xref:Microsoft.Office.Interop.Word.DocumentClass>, обращайтесь к экземпляру интерфейса <xref:Microsoft.Office.Interop.Word.Document>.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 В проекты, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], по умолчанию внедряются все типы из основных сборок взаимодействия Office. Эта ошибка компиляции возникает потому, что типы внедренных сборок взаимодействия работают только с интерфейсами, а не классами. Дополнительные сведения об интерфейсах и классах сборок взаимодействия Office см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592). Дополнительные сведения о компоненте типы внедренных сборок взаимодействия в проектах Office см. в разделе [проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Ссылки на классы Office не распознаются  
 Некоторые имена классов, например приложения, находятся в нескольких пространств имен, такие как <xref:Microsoft.Office.Interop.Word> и <xref:System.Windows.Forms>. По этой причине **Imports**/**с помощью** инструкции в верхней части шаблонов проекта содержит краткую уточняющую константу, например:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 Это использование **Imports**/**с помощью** инструкции необходимо разграничивать ссылки на классы Office с помощью квалификатора Word или Excel, например:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 Ошибки возникают при использовании неполного объявления, например:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 Даже если пространство имен Word или Excel было импортировано и имеют доступ ко всем классам внутри него, необходимо полностью указать все типы в Word или Excel для устранения неоднозначности имен.  
  
##  <a name="building"></a>Построение проектов  
 При сборке проектов Office могут возникнуть следующие ошибки.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Не удается выполнить сборку проекта уровня документа, основанного на документе с ограниченными разрешениями  
 Visual Studio не может выполнить сборку проектов уровня документа с ограниченными разрешениями. Если проект содержит документ с ограниченными разрешениями, проект не будет компилироваться, и вы получите следующее сообщение в **список ошибок** окна.  
  
 "Ошибка при добавлении настройки".  
  
 Если вы хотите добавить документ с ограниченными разрешениями, используйте документ без ограничений при разработке и сборке решения. Затем после публикации решения примените ограниченные разрешения к документу в папке публикации.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Ошибки компиляции возникают после удаления элемента управления NamedRange  
 При удалении элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с неактивного листа в конструкторе невозможно удалить автоматически создаваемый код из проекта, и могут возникать ошибки компилятора. Чтобы удалить код, перед удалением элемента управления необходимо выбрать лист, содержащий элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, чтобы сделать его активным. Если автоматически создаваемый код не удаляется при удалении элемента управления, можно удалить код с помощью конструктора, сделав лист активным и изменив его, чтобы пометить его как измененный. При повторной сборке проекта код удаляется.  
  
##  <a name="debugging"></a>Отладка проектов  
 При отладке проектов Office могут возникнуть следующие ошибки.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>При публикации и установке решения на компьютере разработки появляется запрос на удаление  
 При отладке решения Office может возникнуть следующая ошибка.  
  
 "Не удается установить настройку, поскольку уже установлена другая версия, обновление которой из этой папки невозможно".  
  
 Эта ошибка означает, что вы опубликовали и установили решение Office на компьютере разработки ранее. Чтобы это сообщение не появлялось, перед отладкой решения удалите его из списка установленных программ на компьютере. Или же можно создать другую учетную запись пользователя на компьютере разработки, чтобы протестировать установку опубликованного решения.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Проекты уровня документа, созданные в сетевых расположениях UNC, не запускаются из Visual Studio  
 При создании проекта уровня документа для Excel или Word в сетевом расположении UNC необходимо добавить расположение документа в список надежных расположений в Excel или Word. В противном случае настройки не будут загружаться при запуске или отладке проекта в Visual Studio. Дополнительные сведения о надежных расположениях см. в разделе [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md).  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Неправильная остановка потоков после отладки  
 Проекты Office в Visual Studio следуют соглашению об именовании потоков, которое позволяет отладчику правильно закрывать программу. При создании потоков в решении необходимо присвоить каждому потоку имя с префиксом "VSTA_" для правильной обработки этих потоков при остановке отладки. Например, можно задать `Name` свойства потока, который ожидает сетевые события для **VSTA_NetworkListener**.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Не удается запустить или отладить решение Office на компьютере разработки  
 Если вам не удается запустить или разработать проект Office на компьютере разработки, может появиться следующее сообщение об ошибке:  
  
 "Не удалось загрузить настройку, так как не удалось создать домен приложения".  
  
 Visual Studio использует Fusion, загрузчик сборок платформы .NET Framework, для кэширования сборок перед загрузкой решений Office. Убедитесь, что Visual Studio может записывать данные в кэш Fusion, и повторите попытку. Дополнительные сведения см. в разделе [теневое копирование сборок](/dotnet/framework/app-domains/shadow-copy-assemblies).  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Ошибка при остановке отладчика в проекте уровня документа после использования функции "Изменить и продолжить"  
 Если вы используете функцию "Изменить и продолжить" для внесения изменений в код проекта уровня документа для Excel или Word, когда проект находится в режиме приостановки выполнения, может появиться диалоговое окно со следующим сообщением об ошибке, если впоследствии остановить отладчик:  
  
 "Завершение процесса в его текущем состоянии может привести к нежелательным результатам, включая потерю данных и нестабильность системы".  
  
 Если нажать **Да** или **нет** в диалоговом окне Visual Studio завершает процесс Excel или Word и останавливает отладчик. Чтобы остановить отладку проекта без отображения этого диалогового окна, выйдите из Excel или Word напрямую, а не останавливайте отладчик в Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)   
 [Устранение неполадок безопасности решений Office](../vsto/troubleshooting-office-solution-security.md)   
 [Устранение неполадок, связанных с развертыванием решения Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  
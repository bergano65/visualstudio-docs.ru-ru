---
title: "Пошаговое руководство. Привязка к данным из службы в проекте надстройки VSTO | Microsoft Docs"
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
  - "базы данных [разработка решений Office в Visual Studio], прокрутка записей"
  - "записи [разработка решений Office в Visual Studio], прокрутка"
  - "данные [разработка решений Office в Visual Studio], прокрутка записей базы данных"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Пошаговое руководство. Привязка к данным из службы в проекте надстройки VSTO
  Вы можете привязывать данные к элементам управления ведущего приложения в проектах надстроек VSTO. В этом пошаговом руководстве демонстрируется добавление элементов управления в документ Microsoft Office Word, привязка элементов управления к данным, полученным из службы содержимого MSDN, и реагирование на события во время выполнения.  
  
 **Применение.** Сведения этого раздела относятся к проектам уровня приложения для Word 2010. Для получения дополнительной информации см. [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Добавление элемента управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в документ во время выполнения.  
  
-   Привязка элемента управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl> к данным из веб\-службы.  
  
-   Реагирование на событие <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> элемента управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Создание нового проекта  
 Первым шагом является создание проекта надстройки Word VSTO.  
  
#### Создание нового проекта  
  
1.  Создайте проект надстройки VSTO для Word с именем **Служба содержимого MTPS** в Visual Basic или C\#.  
  
     Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет файл `ThisAddIn.vb` или `ThisAddIn.cs` и добавит проект в **обозреватель решений**.  
  
## Добавление веб\-службы  
 Для этого пошагового руководства используйте веб\-службу, называемую службой содержимого MTPS. Эта веб\-служба возвращает сведения из указанной статьи MSDN в виде строки XML или обычного текста. Ниже показано, как отобразить возвращенные сведения в элементе управления содержимым.  
  
#### Добавление службы содержимого MTPS в проект  
  
1.  В меню **Данные** выберите команду **Добавить новый источник данных**.  
  
2.  В **мастере настройки источника данных** щелкните элемент **Служба** и нажмите кнопку **Далее**.  
  
3.  В поле **Адрес** введите следующий URL\-адрес:  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  Нажмите **Перейти**.  
  
5.  В поле **Пространство имен** введите **ContentService** и нажмите кнопку **ОК**.  
  
6.  В диалоговом окне **Мастер добавления ссылок** нажмите кнопку **Готово**.  
  
## Добавление элемента управления содержимым и привязки к данным во время выполнения  
 В проектах надстроек VSTO вы можете добавлять и привязывать элементы управления во время выполнения. Для этого пошагового руководства настройте элемент управления содержимым для получения данных из веб\-службы, когда пользователь щелкает внутри элемента управления.  
  
#### Добавление элемента управления содержимым и привязка к данным  
  
1.  В классе `ThisAddIn` объявите переменные для службы содержимого MTPS, элемента управления содержимым и привязки данных.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  Добавьте следующий метод в класс `ThisAddIn`. Этот метод создает элемент управления содержимым в начале активного документа.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  Добавьте следующий метод в класс `ThisAddIn`. Этот метод инициализирует объекты, необходимые для создания и отправки запроса в веб\-службу.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  Создайте обработчик событий, чтобы извлечь документ библиотеки MSDN об элементах управления содержимым, когда пользователь щелкает внутри элемента управления, и привяжите данные к элементу управления содержимым.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  Вызовите методы `AddRichTextControlAtRange` и `InitializeServiceObjects` из метода `ThisAddIn_Startup`. Программисты C\# должны добавить обработчик событий.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## Тестирование надстройки  
 При открытии Word появляется элемент управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl>. Текст в этом элементе управления при щелчке внутри него.  
  
#### Тестирование надстройки VSTO  
  
1.  Нажмите клавишу **F5**.  
  
2.  Щелкните внутри элемента управления содержимым.  
  
     Информация загружается из службы содержимого MTPS и отображается внутри элемента управления содержимым.  
  
## См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  
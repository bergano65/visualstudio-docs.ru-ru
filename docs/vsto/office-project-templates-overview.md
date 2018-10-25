---
title: Общие сведения о шаблонах проектов Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1ad35b9aecc9e7559902104f447cbbec3415b49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934331"
---
# <a name="office-project-templates-overview"></a>Общие сведения о шаблонах проектов Office
  Средства разработки для Microsoft Office в Visual Studio включают в себя шаблоны проектов, предназначенные для создания указанных ниже типов решений Office.  
  
- [Настройки уровня документа.](#DocLevel)  
  
- [Надстройки VSTO](#AppLevel)  
  
  Подробное сравнение решений Office этих типов, см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
  Шаблоны проектов Office доступны в диалоговом окне **Создать проект** в узле **Office** узлов языков программирования **Visual C#** и **Visual Basic** . Каждый шаблон создает для целевого приложения проект с соответствующей конфигурацией, включая ссылки на сборку и параметры отладки.  
  
  В каждом проекте имеются файлы и код, необходимые, чтобы приступить к работе над конкретным типом решения. Созданный код для каждого проекта содержит обработчики событий запуска и завершения работы. В эти обработчики событий можно добавить код для инициализации решения при его загрузке и для очистки решения при его выгрузке. Дополнительные сведения см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) и [события в проектах Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Средства разработки для Office входят в некоторые выпуски Visual Studio. Дополнительные сведения см. в разделе [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a> Настройки уровня документа  
 В узле **Office** диалогового окна **Создать проект** имеются указанные ниже шаблоны проектов, позволяющие приступить к работе над созданием настроек на уровне документа для приложений Word и Excel.  
  
- **Документ VSTO для Word 2013 и 2016**  
  
- **Шаблон VSTO для Word 2013 и 2016**  
  
- **Книга VSTO для Excel 2013 и 2016**  
  
- **Шаблон VSTO для Excel 2013 и 2016**  
  
- **Документ VSTO для Word 2010**  
  
- **Шаблон VSTO для Word 2010**  
  
- **Книга VSTO для Excel 2010**  
  
- **Шаблон VSTO для Word 2010**  
  
  Шаблоны проектов "Документ Word" и "Книга Excel" содержат код, позволяющий начать создавать решение, основанное на определенном документе или книге. В решениях этих типов код выполняется только в том случае, если соответствующий документ открыт в приложении Word или Excel.  
  
  Поведение шаблонов проектов "Шаблон Word" и "Шаблон Excel" идентично поведению шаблонов проектов "Документ Word" и "Книга Excel". Однако шаблоны проектов "Шаблон Word" и "Шаблон Excel" облегчают пользователям задачу создания в решении новых локальных копий документа или книги на основе настроенного шаблона. Функциональные возможности решения доступны в новых документах, создаваемых пользователем на основе этого шаблона.  
  
> [!NOTE]  
>  Шаблоны Word, ссылающиеся на расширения управляемого кода, нельзя использовать в качестве глобальных надстроек VSTO. Если шаблон загружается из каталога Startup приложения Word, сборка не вызывается. Дополнительные сведения см. в разделе [ограничения глобальных шаблонов и надстроек Excel (XLA-файлов)](#Limitations)  
  
 Сведения о том, как приступить к работе над проектами этих типов, см. в указанных ниже разделах.  
  
-   [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)  
  
-   [Решения Word](../vsto/word-solutions.md)  
  
-   [Решения Excel](../vsto/excel-solutions.md)  
  
-   [Пошаговое руководство: Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> Надстройки VSTO  
 В узле **Office/SharePoint** в диалоговом окне **Создание проекта** имеются указанные ниже шаблоны проектов, позволяющие приступить к работе по созданию надстроек VSTO.  
  
- **Надстройка VSTO для Excel 2013 и 2016**  
  
- **Надстройка VSTO для InfoPath 2013**  
  
- **Надстройка VSTO для Outlook 2013 и 2016**  
  
- **Надстройка PowerPoint 2013 и 2016**  
  
- **Надстройка Project 2013 и 2016**  
  
- **Надстройка Visio 2013 и 2016**  
  
- **Надстройка Word 2013 и 2016**  
  
- **Надстройка Excel 2010**  
  
- **Надстройка InfoPath 2010**  
  
- **Надстройка Outlook 2010**  
  
- **Надстройка PowerPoint 2010**  
  
- **Надстройка Project 2010**  
  
- **Надстройка Visio 2010**  
  
- **Надстройка Word 2010**  
  
  При создании проекта на основе этих шаблонов проектов код решения выполняется, когда открыто соответствующее приложение. В отличие от проектов уровня документа, код не связан с конкретным документом.  
  
  Дополнительные сведения о том, как приступить к работе над проектами этих типов, см. в указанных ниже разделах.  
  
- [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)  
  
- [Пошаговое руководство: Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Пошаговое руководство по Созданию вашей первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Пошаговое руководство по Созданию вашей первой надстройки VSTO для проекта](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Пошаговое руководство: Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>Документирование и шаблон решения  
 При разработке решения для документа Word или книги Excel следует выбрать оптимальный способ обеспечения доступа к документу для пользователей.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 В некоторых ситуациях может потребоваться раздать копии документа всем пользователям. В этом случае следует создавать решение с помощью проекта документа Excel или Word.  
  
 В других ситуациях потребуется создать шаблон, размещенный на сервере, чтобы каждый пользователь мог открыть его и сохранить локальную копию в виде документа. В этом случае следует создавать решение с помощью проекта шаблона Excel или Word.  
  
## <a name="comparison"></a>Сравнение  
 В следующей таблице приведены различия между документами и шаблонами:  
  
|Документы|Шаблоны|  
|---------------|---------------|  
|Пользователи могут открывать и редактировать документ, если только для него не установлен атрибут "только для чтения". Любые сохраненные изменения сохраняются в исходном документе.|Пользователи могут открывать шаблон, чтобы создать локальную копию в виде нового документа. Они не могут редактировать исходный документ, если у них нет специальных разрешений.|  
|При открытии документа возникает событие <xref:Microsoft.Office.Tools.Word.Document.Open> .|При открытии шаблона возникает событие <xref:Microsoft.Office.Tools.Word.Document.New> .|  
  
##  <a name="Limitations"></a> Ограничения глобальных шаблонов и надстроек Excel (XLA-файлов)  
 Документы, книги и шаблоны могут работать неправильно в качестве глобальных шаблонов или надстроек VSTO для Excel (XLA-файлов).  
  
## <a name="word-templates"></a>Шаблоны Word  
 Если шаблон Microsoft Office Word имеет расширения управляемого кода, сборка проекта не вызывается, если этот шаблон подключен как глобальный шаблон или загружен из каталога автозагрузки Word. Кроме того, документ не распознает формат шаблона, являющегося частью решения Office.  
  
## <a name="excel-add-ins-xla-files"></a>Надстроек Excel (XLA-файлов)  
 Нет Office проекта по созданию надстройки VSTO для Excel (*.xla* файла). Можно сохранить книгу как XLA-файл, но эта операция не поддерживается и не рекомендуется. Если вы сохраните книгу, имеющую расширения управляемого кода как **Microsoft Office Excel Add-In (\*.xla)** файл, можно выбрать его в **Add-Ins** диалоговое окно, чтобы применить к другой книге. В некоторых случаях код будет выполняться в целевой книге, после применения надстройки VSTO, но такое решение Office не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступить к программированию настроек на уровне документа для Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Приступить к программированию настроек на уровне документа для Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
---
title: "Пользовательских XML-частях Обзор | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 735660c3af1c0a8792a35981788b70f4a79d55b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="custom-xml-parts-overview"></a>Custom XML Parts Overview
  Для некоторых приложений Microsoft Office в документах можно внедрять XML-данные. При внедрении в документ XML-данных, называются *пользовательской XML-части*.  
  
 Для создания и изменения пользовательских XML-частей в документе можно использовать надстройку VSTO или решение в Visual Studio на уровне документа. Для создания и изменения пользовательских XML-частей запускать приложение Microsoft Office не требуется.  
  
 **Применяется к:** информация в этой статье относится к проектам уровня документа и проектам надстроек VSTO для Excel, PowerPoint и Word. Дополнительные сведения см. в разделе [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio также позволяет кэшировать объекты данных в настройках на уровне документа. Несмотря на некоторые сходства, эта возможность отличается от пользовательских XML-частей. Дополнительные сведения см. в разделе [кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understanding-custom-xml-parts"></a>Основные сведения о пользовательских XML-частях  
 Пользовательские XML-части впервые появились в системе Microsoft Office 2007 вместе с форматами Open XML. К этим форматам относятся новые форматы файлов на основе XML для Excel, PowerPoint и Word (XLSX, PPTX и DOCX). Документы в этих форматах состоят из XML-файлов (также называемых *XML-части*), которые располагаются в папках в ZIP-архиве. Большинство XML-частей представляют собой встроенные части, позволяющие определить структуру и состояние документа. Однако документы также могут содержать пользовательские XML-части, которые можно использовать для хранения произвольных XML-данных в документах.  
  
 Форматы XML-файлов позволяют приложениям работать с документами по-новому, не так как со старыми форматами двоичных файлов (например, XLS, PPT и DOC). Любое приложение, которое может читать ZIP-архивы, может проверять и изменять содержимое документов даже в том случае, если Microsoft Office не установлен.  
  
 Дополнительные сведения о структуре Open XML и пользовательских XML-частей см. в следующих статьях.  
  
-   [Знакомство с форматами файлов Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Как: управления документов в форматах Open XML](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Пошаговое руководство: Формат Word 2007 XML](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Построение документов Word 2007 с помощью Open XML форматы](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word и PowerPoint также позволяют использовать пользовательские XML-части в документах, которые были сохранены в форматах двоичных файлов. Однако, если документ сохранен в двоичном формате, для добавления или изменения пользовательских XML-частей необходимо запустить приложение Microsoft Office.  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>Создание и изменение пользовательских XML-частей  
 Пользовательские XML-части можно создавать или изменять, когда документ открыт в приложении Office или когда документ закрыт (даже если Microsoft Office не установлен).  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Изменение XML-частей, когда приложение Office работает  
 Для работы с пользовательскими XML-частями можно использовать настройку на уровне документа или надстройку VSTO. При использовании настройки на уровня документе работа обычно ведется с теми пользовательскими XML-частями, которые находятся в настроенном документе. С помощью надстройки VSTO можно создавать или изменять пользовательские XML-части в любом документе, который открыт в приложении.  
  
 Для создания пользовательской XML-части с помощью Visual Studio добавьте новую <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в документе. Дополнительные сведения см. в следующих разделах:  
  
-   [Практическое руководство. Добавление настраиваемых частей XML в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Практическое руководство. Добавление настраиваемых частей XML в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Изменение XML-частей без запуска приложения Office  
 Пользовательские XML-части можно добавлять или изменять без запуска Excel, PowerPoint или Word. Это удобно в том случае, если вам нужно работать с XML-данными в документе на компьютере, на котором приложения Microsoft Office не установлены, например на сервере.  
  
 Для добавления пользовательской XML-части без запуска Microsoft Office используйте классы в пакете SDK для Open XML. Эти классы предоставляют доступ к содержимому Open XML, характерному для документов Office. Например, для добавления пользовательской XML-части в книгу Excel, используйте [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) метод [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) объекта. Дополнительные сведения см. в разделе [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Привязка пользовательских XML-частей к элементам управления содержимым Word  
 Элементы управления содержимым в решении Word можно привязать к элементам в пользовательской XML-части. Если элемент управления содержимым привязан к пользовательской XML-части, ее данные отображаются в пользовательском интерфейсе элемента управления содержимым. Если пользователь редактирует текст в элементе управления, автоматически обновляется соответствующий XML-элемент. Аналогичным образом, если значения элементов в пользовательских XML-частях изменяются, элементы управления содержимым, привязанные к XML-элементам, отображают новые данные. Для получения дополнительной информации см. [Content Controls](../vsto/content-controls.md).  
  
## <a name="see-also"></a>См. также  
 [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Как: Добавление пользовательских XML-частей в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Как: Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  
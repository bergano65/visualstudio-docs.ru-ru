---
title: Общие сведения о настраиваемых частях XML
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94deacad38f40d76b4c8485186bfd563808d912
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445525"
---
# <a name="custom-xml-parts-overview"></a>Общие сведения о настраиваемых частях XML
  Для некоторых приложений Microsoft Office в документах можно внедрять XML-данные. При внедрении в документ XML-данных, называются *пользовательской XML-части*.

 Для создания и изменения пользовательских XML-частей в документе можно использовать надстройку VSTO или решение в Visual Studio на уровне документа. Для создания и изменения пользовательских XML-частей запускать приложение Microsoft Office не требуется.

 **Область применения:** Сведения этого раздела применяются к проектам уровня документа и надстройками VSTO для Excel, PowerPoint и Word. Дополнительные сведения см. в разделе [функций по типам приложений и проектов Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Visual Studio также позволяет кэшировать объекты данных в настройках на уровне документа. Несмотря на некоторые сходства, эта возможность отличается от пользовательских XML-частей. Дополнительные сведения см. в разделе [кэшированных данных в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Понять, настраиваемые XML-части
 Пользовательские XML-части впервые появились в системе Microsoft Office 2007 вместе с форматами Open XML. К этим форматам относятся новые форматы файлов на основе XML для Excel, PowerPoint и Word (такие как *.xlsx*, *.pptx*, и *.docx*). Документы в этих форматах состоят из XML-файлов (также называется *XML-частям*), которые располагаются в папках в ZIP-архиве. Большинство XML-частей представляют собой встроенные части, позволяющие определить структуру и состояние документа. Однако документы также могут содержать пользовательские XML-части, которые можно использовать для хранения произвольных XML-данных в документах.

 XML-файле форматирует предоставлять приложениям возможность работы с документами, таким образом, невозможно использовать в старыми форматами двоичных файлов (таких как *.xls*, *.ppt*, и *.doc*). Любое приложение, которое может читать ZIP-архивы, может проверять и изменять содержимое документов даже в том случае, если Microsoft Office не установлен.

 Дополнительные сведения о структуре Open XML и пользовательских XML-частей см. в следующих статьях.

- [Знакомство с форматами файлов Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Практическое руководство. Управлять документами в форматах Open XML](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Пошаговое руководство: Формат Word 2007 XML](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Построение документов Word 2007 с помощью форматов Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word и PowerPoint также позволяют использовать пользовательские XML-части в документах, которые были сохранены в форматах двоичных файлов. Однако, если документ сохранен в двоичном формате, для добавления или изменения пользовательских XML-частей необходимо запустить приложение Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Создание и изменение пользовательских XML-частей
 Пользовательские XML-части можно создавать или изменять, когда документ открыт в приложении Office или когда документ закрыт (даже если Microsoft Office не установлен).

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Изменения XML-частей, во время работы приложения Office
 Можно работать с пользовательскими частями XML с помощью настройки уровня документа или надстройки VSTO. При использовании настройки на уровня документе работа обычно ведется с теми пользовательскими XML-частями, которые находятся в настроенном документе. При использовании надстройки VSTO, можно создать или изменить пользовательские XML-части в любом документе, который открыт в приложении.

 Для создания пользовательской XML-части с помощью Visual Studio добавьте новую <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в документе. Дополнительные сведения см. в следующих разделах:

- [Практическое руководство. Добавление пользовательских частей XML в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Изменения XML-частей без запуска приложения Office
 Пользовательские XML-части можно добавлять или изменять без запуска Excel, PowerPoint или Word. Это удобно в том случае, если вам нужно работать с XML-данными в документе на компьютере, на котором приложения Microsoft Office не установлены, например на сервере.

 Для добавления пользовательской XML-части без запуска Microsoft Office используйте классы в пакете SDK для Open XML. Эти классы предоставляют доступ к содержимому Open XML, характерному для документов Office. Например, Добавление пользовательской XML-части в книгу Excel, можно использовать <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> метод <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> объекта. Дополнительные сведения см. в разделе [Open XML SDK для](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Привязка пользовательских XML-частей к элементам управления содержимым Word
 Элементы управления содержимым в решении Word можно привязать к элементам в пользовательской XML-части. Если элемент управления содержимым привязан к пользовательской XML-части, ее данные отображаются в пользовательском интерфейсе элемента управления содержимым. Если пользователь редактирует текст в элементе управления, автоматически обновляется соответствующий XML-элемент. Аналогичным образом, если значения элементов в пользовательских XML-частях изменяются, элементы управления содержимым, привязанные к XML-элементам, отображают новые данные. Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

## <a name="see-also"></a>См. также
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Практическое руководство. Добавление пользовательских частей XML в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Элементы управления содержимым](../vsto/content-controls.md)
- [Пошаговое руководство: Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

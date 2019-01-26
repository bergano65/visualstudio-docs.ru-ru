---
title: Разработка решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1aa7be95b0812b27c302500bd166abcb00c7089d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874535"
---
# <a name="develop-office-solutions"></a>Разработка решений Office
  После разработки проекта с помощью Office Developer Tools в Visual Studio и настройки файлов проекта можно начать реализовывать код и пользовательский интерфейс.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с VSTO Add-ins и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="office-solutions-programming-model"></a>Модель программирования решений Office  
 Объектная модель Office предоставляет широкий набор объектов, которые можно использовать. При программировании решений Office с помощью управляемого кода вы создаете код, который использует типы в основных сборках взаимодействия Office. В решениях, создаваемых с помощью шаблонов проектов Office в Visual Studio, также можно разрабатывать код непосредственно для созданных классов в своем проекте. Дополнительные сведения см. в разделе [написания кода в решениях Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Программы различных типов решений Office  
 Тип создаваемого решения определяет, какие функции можно использовать в проекте. Например, элементы управления Windows Forms и расширенные элементы управления Office (которые называются *элементы управления ведущего приложения*) можно добавлять в настройки на уровне документа путем перетаскивания элементов из **панели элементов** в Visual Studio во время разработки. Однако при разработке надстройки VSTO можно только добавлять эти элементы управления в документы во время выполнения путем написания кода.  
  
 Дополнительные сведения о функциях, характерных для различных типов решений, см. в следующих статьях:  
  
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
- [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md).  
  
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
  Для получения дополнительных сведений о планировании решений Office и процедурах создания проектов, см. в разделе [проектирования и создания решений Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)|Описание различных аспектов написания кода в решениях Office.|  
|[Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)|Общие сведения о модели программирования надстроек VSTO и связанных задачах программирования.|  
|[Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)|Общие сведения о модели программирования настроек на уровне документа и связанных задачах программирования.|  
|[Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)|Описание различных способов настройки пользовательского интерфейса приложений Office с помощью надстроек VSTO и настроек на уровне документа.|  
|[Данные в решениях Office](../vsto/data-in-office-solutions.md)|Описание различных способов работы с данными в решениях Office, например, привязки данных к элементам управления и кэширования данных в настройках на уровне документа.|  
|[Как эта функция влияет на решения Office](./how-autosave-impacts-office-solutions.md)|Описывает изменения, которые может потребоваться внести для решений Office, когда включена функция автоматического сохранения.|
|[Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)|Советы по решению типичных проблем, которые могут происходить при создании решений Office.|  
|[Поддержка потоков в Office](../vsto/threading-support-in-office.md)|Общие сведения о работе с несколькими потоками в решениях Office.|  
|[Специальные возможности в проектах Office](../vsto/accessibility-in-office-projects.md)|Описание специальных возможностей, доступных в решениях Office.|  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Пошаговое руководство: Создание вашей первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Пошаговое руководство: Создание вашей первой надстройки VSTO для проекта](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Пошаговое руководство: Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  

---
title: 'Практическое: запретить отображение области формы Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1ec9f45b2055a7a56e067440d216482877da14c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949062"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Практическое: запретить отображение области формы Outlook
  Могут возникнуть ситуации, в которых требуется Microsoft Office Outlook отображение области формы для определенного элемента. Например если элемент контактов не содержит рабочий адрес, можно запретить области формы, показывающий местонахождение бизнеса в схеме.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Для предотвращения отображения области формы Outlook  
  
1. Откройте файл кода для области формы, которую требуется изменить.  
  
2. Разверните **фабрика областей формы** области кода.  
  
3. Добавьте код для `FormRegionInitializing` обработчик событий, который задает <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойство <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> класс **true**.  
  
   В этом примере, если элемент контактов не содержит адрес <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойству **true**, и области формы не отображается.  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>См. также  
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Практическое: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Пошаговое руководство: Импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
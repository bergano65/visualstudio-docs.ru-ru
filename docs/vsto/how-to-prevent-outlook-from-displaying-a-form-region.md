---
title: "Как: запретить отображение области формы Outlook | Документы Microsoft"
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
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb181ba7bd408194bec52224496ebef7f343f5d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Практическое руководство. Отсутствие отображения области формы в Outlook
  Возможны ситуации, в которых требуется Microsoft Office Outlook отображение области формы для конкретного элемента. Например если элемент контактов не содержит рабочий адрес, можно запретить отображение местонахождения предприятия в схеме области формы.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Чтобы предотвратить отображение области формы Outlook  
  
1.  Откройте файл кода для области формы, которую требуется изменить.  
  
2.  Разверните **фабрика областей формы** области кода.  
  
3.  Добавьте код для `FormRegionInitializing` обработчик событий, который задает <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойство <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> класса **true**.  
  
 В этом примере, если элемент контактов не содержит адрес <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойству **true**, и область формы не отображается.  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>См. также  
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
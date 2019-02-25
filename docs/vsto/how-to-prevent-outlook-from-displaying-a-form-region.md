---
title: Практическое руководство. Запретить отображение области формы Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad17041650324e597fb76925f521bb7fc2e9ce93
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629187"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Практическое руководство. Запретить отображение области формы Outlook
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
- [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)
- [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Практическое руководство. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Пошаговое руководство: Импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)

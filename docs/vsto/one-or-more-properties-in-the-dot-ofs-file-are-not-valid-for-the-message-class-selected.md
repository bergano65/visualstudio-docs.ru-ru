---
title: "Одно или несколько свойств OFS-файла являются недопустимыми для выбранного класса сообщений | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6ab0b36921911ac8c70501096868f47a40371f79
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Одно или несколько свойств OFS-файла являются недопустимыми для выбранного класса сообщений
  Эта ошибка выводится, когда вы импортируете область формы, разработанную в Outlook, однако одно или несколько полей в области формы несовместимы с классами сообщений, выбранными на последней странице мастера **Создать область формы** .  
  
 Например, вы могли выбрать тип **Задача (IPM.Task)** на последней странице мастера **Создать область формы** . Если в области формы есть поле **Рабочий адрес** , возникнет эта ошибка, так как у задачи не может быть рабочего адреса. Следовательно, поле **Рабочий адрес** несовместимо с классом сообщений IPM.Task.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   На последней странице мастера **Создать область формы** выберите класс сообщений, который совместим с полями в области формы.  
  
-   В конструкторе форм Outlook удалите поля, несовместимые с классами сообщений, которые вы планируете выбрать на последней странице мастера **Создать область формы** .  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
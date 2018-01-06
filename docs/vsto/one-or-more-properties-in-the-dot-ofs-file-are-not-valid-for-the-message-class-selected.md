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
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ca816a635abf929f2bfa1614f4560f434adbfd45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Одно или несколько свойств OFS-файла являются недопустимыми для выбранного класса сообщений
  Эта ошибка выводится, когда вы импортируете область формы, разработанную в Outlook, однако одно или несколько полей в области формы несовместимы с классами сообщений, выбранными на последней странице мастера **Создать область формы** .  
  
 Например, вы могли выбрать тип **Задача (IPM.Task)** на последней странице мастера **Создать область формы** . Если в области формы есть поле **Рабочий адрес** , возникнет эта ошибка, так как у задачи не может быть рабочего адреса. Следовательно, поле **Рабочий адрес** несовместимо с классом сообщений IPM.Task.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   На последней странице мастера **Создать область формы** выберите класс сообщений, который совместим с полями в области формы.  
  
-   В конструкторе форм Outlook удалите поля, несовместимые с классами сообщений, которые вы планируете выбрать на последней странице мастера **Создать область формы** .  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
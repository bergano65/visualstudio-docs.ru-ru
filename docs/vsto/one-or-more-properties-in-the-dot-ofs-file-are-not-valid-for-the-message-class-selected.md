---
title: Одно или несколько свойств OFS-файла являются недопустимыми для выбранного класса сообщений | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac9f5ab05ba6ed858946b5f665d850eea51c230
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Одно или несколько свойств OFS-файла являются недопустимыми для выбранного класса сообщений
  Эта ошибка выводится, когда вы импортируете область формы, разработанную в Outlook, однако одно или несколько полей в области формы несовместимы с классами сообщений, выбранными на последней странице мастера **Создать область формы** .  
  
 Например, вы могли выбрать тип **Задача (IPM.Task)** на последней странице мастера **Создать область формы** . Если в области формы есть поле **Рабочий адрес** , возникнет эта ошибка, так как у задачи не может быть рабочего адреса. Следовательно, поле **Рабочий адрес** несовместимо с классом сообщений IPM.Task.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   На последней странице мастера **Создать область формы** выберите класс сообщений, который совместим с полями в области формы.  
  
-   В конструкторе форм Outlook удалите поля, несовместимые с классами сообщений, которые вы планируете выбрать на последней странице мастера **Создать область формы** .  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
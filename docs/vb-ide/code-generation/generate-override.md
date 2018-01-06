---
title: "Создать переопределение - формирования кода (Visual Basic) | Документы Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a384eb3e75a499eb2a35c747f003846580738e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Переопределение создания в Visual Basic
**Что:** позволяет немедленно создания кода для любого метода, который можно переопределить из базового класса. 

**Когда:** необходимо переопределить метод базового класса и автоматического создания подписи.  

**Почему:** можно написать сигнатуре метода самостоятельно, однако эта функция автоматически создаст подпись. 

**Как:**

1. Тип **переопределяет** ключевого слова, за которыми следует пробел, где вы хотите вставить подпись переопределенного метода, и появится раскрывающийся список IntelliSense.

   ![Переопределить IntelliSense](media/override_intellisense.png)

1. Выберите метод, который вы хотите переопределить от базового класса, щелкнув его с помощью мыши или перейдя на него с помощью клавиатуры и нажав клавишу **ввод**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. Выбранный метод или свойство будет добавлен в класс как override, Готово к реализации.

   ![Переопределить результат](media/override_result.png)

## <a name="see-also"></a>См. также  
[Создание кода (Visual Basic)](../code-generation-vb.md) 
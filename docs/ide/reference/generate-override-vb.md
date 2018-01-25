---
title: "Создание переопределения — создание кода (Visual Basic) | Документация Майкрософт"
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
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Создание переопределения в Visual Basic
**Что.** Немедленное создание кода для любого метода, который можно переопределить из базового класса. 

**Когда.** Необходимо переопределить метод базового класса и автоматически создать подпись.  

**Зачем.** Сигнатуру метода можно написать самостоятельно, но эта функция автоматически создает подпись. 

**Как.**

1. Введите ключевое слово **Переопределения**, за которым следует пробел, там, где нужно вставить подпись переопределенного метода. Появится раскрывающийся список IntelliSense.

   ![Переопределение IntelliSense](media/override-intellisense-vb.png)

1. Выберите метод, который вы хотите переопределить из базового класса. Для этого щелкните его с помощью мыши или перейдите на него с помощью клавиатуры и нажмите клавишу **ВВОД**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. Выбранный метод или свойство будет добавлено в класс как переопределение, готовое к реализации.

   ![Результат переопределения](media/override-result-vb.png)

## <a name="see-also"></a>См. также

[Создание кода](../code-generation-in-visual-studio.md) 
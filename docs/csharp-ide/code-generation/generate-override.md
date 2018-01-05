---
title: "Создать переопределение - формирования кода (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 622c05f51d0dc32739f5d27b75aec31c69ee4d87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-c"></a>Создать переопределение в C# #

**Что:** позволяет немедленно создать код для любого метода, который можно переопределить из базового класса.

**Когда:** необходимо переопределить метод базового класса и автоматического создания подписи.

**Почему:** можно написать сигнатуре метода самостоятельно, однако эта функция автоматически создаст подпись.

**Как:**

1. Тип **переопределить** ключевого слова, за которыми следует пробел, где вы хотите вставить подпись переопределенного метода, и появится раскрывающийся список IntelliSense.

   ![Переопределить IntelliSense](media/override_intellisense.png)

1. Выберите метод, который вы хотите переопределить от базового класса, щелкнув его с помощью мыши или перейдя на него с помощью клавиатуры и нажав клавишу **ввод**.

   >[!TIP]
   >* Значок «свойство» ![Значок свойства](media/override_property.png) Чтобы отобразить или скрыть свойства в списке.
   >* Использовать значок метода ![Значок метода](media/override_method.png) Чтобы отобразить или скрыть методы в списке.

1. Выбранный метод или свойство будет добавлен в класс как override, Готово к реализации.

   ![Переопределить результат](media/override_result.png)

## <a name="see-also"></a>См. также

[Создание кода (C#)](../code-generation-csharp.md)

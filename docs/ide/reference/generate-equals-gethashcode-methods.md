---
title: Создание переопределений для методов Equals и GetHashCode C# в Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9af687eb4b39afdbe9fd34df1aa03f18ce243ef8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903118"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Создание переопределений для методов Equals и GetHashCode в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Эта возможность позволяет создавать методы **Equals** и **GetHashCode**.

**Когда?** Создавайте эти переопределения, если у вас есть тип, который нужно сравнить по одному или нескольким полям, а не по расположению объектов в памяти.

**Зачем?**

- Если вы реализуете тип значения, рекомендуем переопределить метод **Equals**, чтобы повысить производительность по сравнению со стандартной реализацией метода Equals в ValueType.

- При реализации ссылочного типа рекомендуем переопределить метод **Equals**, если ваш тип выглядит как базовый, например Point, String, BigNumber и т. д.

- Переопределите метод **GetHashCode**, чтобы тип правильно работал в хэш-таблице. Дополнительные сведения см. в руководстве по [операторам равенства](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Практические советы

1. Поместите курсор в объявление типа.

   ![Выделенный код](media/overrides-highlight-cs.png)

1. Затем выполните одно из следующих действий:

   - **Клавиатура**
      - Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.
   - **Мышь**
      - Щелкните правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.
      - Нажмите кнопку ![Значок лампочки](media/bulb-cs.png) который отображается в поле слева, если текстовый курсор уже находится в строке выбора с объявлением типа.

   ![Создание переопределений — предварительный просмотр](media/overrides-preview-cs.png)

1. Выберите **Создать Equals(object)** или **Создать Equals и GetHashCode** в раскрывающемся меню.

1. В диалоговом окне **Выбрать члены** выберите члены, для которых хотите создать методы:

    ![Диалоговое окно создания переопределений](media/overrides-dialog-cs.png)

    > [!TIP]
    > В этом диалоговом окне также можно создавать операторы, используя флажки под списком элементов.

   Переопределения Equals и GetHashCode создаются с реализациями по умолчанию.

   ![Результат создания метода](media/overrides-result-cs.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
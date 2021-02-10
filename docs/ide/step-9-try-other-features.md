---
title: Шаг 9. Изучение других возможностей
description: Узнайте, как изменить значки и цвета, добавить в игру таймер или звуки и увеличить игровую доску.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e405cef9360083a8f0169ac338e2c23cffc71218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969559"
---
# <a name="step-9-try-other-features"></a>Шаг 9. Изучение других возможностей
Для изучения других функций попробуйте изменить значки и цвета, добавить в игру таймер или звуки. Чтобы сделать игру интереснее, увеличьте игровое поле или измените настройки таймера.

Скачать готовую версию примера можно на странице с [полным примером руководства по созданию игры](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Изучение других возможностей

- Замените значки и цвета на другие.

    > [!TIP]
    > Попробуйте проверить свойство [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) метки.

- Добавьте таймер игры, который отслеживает время, необходимое игроку для победы.

    > [!TIP]
    > Для этого можно добавить метку для отображения истекшего времени в форму над элементом <xref:System.Windows.Forms.TableLayoutPanel> и добавить в форму еще один таймер для отслеживания времени. Следующий код служит для запуска таймера, когда игрок начинает игру, и остановки таймера после сопоставления последних двух значков.

- Добавьте звуки, которые будут воспроизводиться при нахождении игроком пары, отображении двух несовпадающих значков и повторном сокрытии значков программой.

    > [!TIP]
    > Для воспроизведения звуков можно использовать пространство имен <xref:System.Media>. Дополнительные сведения см. в руководстве по воспроизведению звуков в [приложении Windows Forms (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) и [Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be).

- Сделайте игру труднее, увеличив игровое поле.

    > [!TIP]
    > Необходимо не только добавить строки и столбцы в TableLayoutPanel, но и учесть количество создаваемых значков.

- Сделайте игру интереснее, скрывая первый значок, если игрок действует медленно и не щелкает второй значок в течение определенного времени.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Также вы можете найти отличные бесплатные учебные видеоматериалы. Дополнительные сведения о программировании на Visual Basic см. в руководстве по [разработке на Visual Basic для начинающих](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Дополнительные сведения о программировании на языке C# см. в разделе [Основы C#. Разработка для начинающих](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Предыдущий раздел: [Шаг 8. Добавление метода проверки выигрыша игрока](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

---
title: Шаг 9. Изучение других возможностей
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff87247afb79d62867da9e55f7a059192789d79
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118842"
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
    > Для воспроизведения звуков можно использовать пространство имен <xref:System.Media>. Дополнительные сведения см. в руководстве по воспроизведению звуков в [приложении Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) и [Visual Basic](http://youtu.be/-4oPDeQrtMs).

- Сделайте игру труднее, увеличив игровое поле.

    > [!TIP]
    > Необходимо не только добавить строки и столбцы в TableLayoutPanel, но и учесть количество создаваемых значков.

- Сделайте игру интереснее, скрывая первый значок, если игрок действует медленно и не щелкает второй значок в течение определенного времени.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Если у вас возникли затруднения или вопросы по программированию, попробуйте задать вопрос на одном из форумов MSDN. См. [форум по Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) и [форум по Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- Также вы можете найти отличные бесплатные учебные видеоматериалы. Дополнительные сведения о программировании на Visual Basic см. в руководстве [Основы Visual Basic. Разработка для начинающих](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Дополнительные сведения о программировании на языке Visual C# см. в разделе [Основы C#. Разработка для начинающих](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Предыдущий раздел руководства: [Шаг 8. Добавление метода для проверки того, выиграл ли игрок](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

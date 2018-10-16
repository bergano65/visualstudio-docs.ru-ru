---
title: Шаг 9. Изучение других возможностей
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc842af3723a8b056d1de684bd798f4fda37cff8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2018
ms.locfileid: "32065082"
---
# <a name="step-9-try-other-features"></a>Шаг 9. Изучение других возможностей
Для изучения других функций попробуйте изменить значки и цвета, добавить в игру таймер или звуки. Чтобы сделать игру интереснее, увеличьте игровое поле или измените настройки таймера.  
  
 Скачать готовую версию примера можно на странице с [полным примером руководства по созданию игры](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
## <a name="to-try-other-features"></a>Изучение других возможностей  

-   Замените значки и цвета на другие.  

    > [!TIP]
    >  Попробуйте проверить свойство [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) метки.  

-   Добавьте таймер игры, который отслеживает время, необходимое игроку для победы.  

    > [!TIP]
    >  Для этого можно добавить метку для отображения истекшего времени в форму над элементом <xref:System.Windows.Forms.TableLayoutPanel> и добавить в форму еще один таймер для отслеживания времени. Следующий код служит для запуска таймера, когда игрок начинает игру, и остановки таймера после сопоставления последних двух значков.  

-   Добавьте звуки, которые будут воспроизводиться при нахождении игроком пары, отображении двух несовпадающих значков и повторном сокрытии значков программой.  

    > [!TIP]
    >  Для воспроизведения звуков можно использовать пространство имен <xref:System.Media>. Дополнительные сведения см. в руководстве по воспроизведению звуков в [приложении Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) и [Visual Basic](http://youtu.be/-4oPDeQrtMs).  
  
-   Сделайте игру труднее, увеличив игровое поле.  

    > [!TIP]
    >  Необходимо не только добавить строки и столбцы в TableLayoutPanel, но и учесть количество создаваемых значков.  

-   Сделайте игру интереснее, скрывая первый значок, если игрок действует медленно и не щелкает второй значок в течение определенного времени.  

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Если у вас возникли затруднения или вопросы по программированию, попробуйте задать вопрос на одном из форумов MSDN. См. [форум по Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) и [форум по Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Также вы можете найти отличные бесплатные учебные видеоматериалы. Дополнительные сведения о программировании на Visual Basic см. в руководстве по [разработке на Visual Basic для начинающих](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Дополнительные сведения о программировании на Visual C# см. в руководстве по [разработке на Visual C# для начинающих](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Предыдущий раздел: [Шаг 8. Добавление метода проверки выигрыша игрока](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

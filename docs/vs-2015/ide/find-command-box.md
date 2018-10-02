---
title: Поле "Найти/Команда" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22ced396f8a18cf2a665ed7a1ba1016b16e44c8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560529"
---
# <a name="findcommand-box"></a>Поиск/Команда - окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [окно Find-Command](https://docs.microsoft.com/visualstudio/ide/find-command-box).  
  
В поле **Найти/Команда** можно искать текст и выполнять команды Visual Studio. Поле **Найти/Команда** по-прежнему доступно как элемент управления панели инструментов, но больше не отображается по умолчанию. Поле **Найти/Команда** можно отобразить, выбрав на **стандартной** панели инструментов команду **Добавить или удалить кнопки** и щелкнув **Найти**.  
  
 Чтобы выполнить команду [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], введите перед ней знак "больше, чем" (>).  
  
 В поле **Найти/Команда** сохраняются последние 20 введенных элементов, которые выводятся в раскрывающемся списке. Перемещаться по списку можно с помощью клавиш со стрелками.  
  
 ![Поле "Найти&#47;Команда"](../ide/media/findcommandbox.png "FindCommandBox")  
Поиск/Команда - окно  
  
## <a name="searching-for-text"></a>Поиск текста  
 После ввода текста в поле **Найти/Команда** и нажатии клавиши ВВОД среда Visual Studio по умолчанию выполняет поиск в текущем документе или окне инструментов с использованием параметров, указанных в диалоговом окне **Поиск в файлах**. Для получения дополнительной информации см. [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Ввод команд  
 Чтобы с помощью поля **Найти/Команда** выполнить отдельную команду или псевдоним [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], а не поиск текста, введите команду [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], указав перед ней знак "больше, чем" (>). Пример:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Кроме того, для ввода и выполнения отдельных или нескольких команд можно использовать окно "Команда". Некоторые команды и псевдонимы можно вводить и выполнять сами по себе, в то время как синтаксис других включает обязательные аргументы. Список команд с аргументами см. в разделе [Команды Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Escape-символы  
 Символ "крышки" (^) в командной строке означает, что следующий за ним символ интерпретируется буквально, а не как управляющий символ. Благодаря этому в значение параметра можно внедрить прямые кавычки ("), пробелы, начальные символы косой черты, крышки или другие знаки, за исключением имен параметров. Например, примененная к объекту директива  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Крышка действует одинаково как внутри кавычек, так и за их пределами. Если крышка является последним символом в строке, она игнорируется.  
  
## <a name="see-also"></a>См. также  
 [Командное окно](../ide/reference/command-window.md)   
 [Поиск и замена текста](../ide/finding-and-replacing-text.md)




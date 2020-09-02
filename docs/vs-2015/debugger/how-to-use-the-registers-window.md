---
title: Как использовать окно "регистры" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697467"
---
# <a name="how-to-use-the-registers-window"></a>Практическое руководство. Использование окна регистров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно Регистры доступно только при включении отладки на уровне адреса в категории **Общие** узла **Отладка** диалогового окна **Параметры**.  
  
 В окне **регистры** отображается содержимое регистров. Если окно **регистров** не открывается при пошаговом выполнении программы, можно увидеть, что значения регистров изменяются по мере выполнения кода. Значения, которые недавно изменились, отображаются красным цветом. Значения регистров можно изменять. Дополнительные сведения см. [в разделе инструкции. изменение значения регистра](../debugger/how-to-edit-a-register-value.md).  
  
 Для упорядочивания регистры в окне **Регистры** объединены в группы, которые зависят от платформы и типа процессора. При желании группы можно отображать или скрывать. Дополнительные сведения см. [в разделе как отображать и скрывать группы регистров](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Общие сведения об основных понятиях регистров и окне регистров см. в разделе [Основные сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Отображение окна регистров  
  
- В меню **Отладка** выберите пункт **окна**, а затем щелкните **регистры**.  
  
     Отладчик должен быть запущен либо находиться в режиме приостановки выполнения.  
  
    > [!NOTE]
    > Для скриптов и приложений SQL сведения о регистрах недоступны.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Основные сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)

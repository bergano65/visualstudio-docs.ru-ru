---
title: Практическое руководство. Использование окна регистров | Документация Майкрософт
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697467"
---
# <a name="how-to-use-the-registers-window"></a>Практическое руководство. Использование окна регистров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно "Регистры" доступно только в том случае, если включена отладка на уровне адреса в **параметры** диалоговом окне **Отладка** узел, **Общие** категории.  
  
 **Регистрирует** окне отображается содержимое регистров. Если вы храните **регистрирует** окно открыто при пошаговой отладке программы, вы увидите изменение значений регистров по ходу выполнения. Значения, которые недавно изменились, отображаются красным цветом. Значения регистров можно изменять. Дополнительные сведения см. в разделе [Практическое руководство. Изменение значения регистра](../debugger/how-to-edit-a-register-value.md).  
  
 Для упорядочивания регистры в окне **Регистры** объединены в группы, которые зависят от платформы и типа процессора. При желании группы можно отображать или скрывать. Дополнительные сведения см. в разделе [Практическое руководство. Отображение и скрытие групп регистров](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Обобщенный Обзор в принципы использования регистров и окна регистров, см. в разделе [основы отладки: Регистрирует окно](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Отображение окна регистров  
  
- На **Отладка** меню, выберите **Windows**, а затем выберите **регистрирует**.  
  
     Отладчик должен быть запущен либо находиться в режиме приостановки выполнения.  
  
    > [!NOTE]
    > Для скриптов и приложений SQL сведения о регистрах недоступны.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об отладке: Окно "Регистры"](../debugger/debugging-basics-registers-window.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)

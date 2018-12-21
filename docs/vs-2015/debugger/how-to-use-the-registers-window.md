---
title: 'Практическое: использование окна регистров | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6856b2e10c43f33e22711353d33f732779e8f4af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748124"
---
# <a name="how-to-use-the-registers-window"></a>Практическое руководство. Использование окна регистров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно "Регистры" доступно только в том случае, если включена отладка на уровне адреса в **параметры** диалоговом окне **Отладка** узел, **Общие** категории.  
  
 **Регистрирует** окне отображается содержимое регистров. Если вы храните **регистрирует** окно открыто при пошаговой отладке программы, вы увидите изменение значений регистров по ходу выполнения. Значения, которые недавно изменились, отображаются красным цветом. Значения регистров можно изменять. Дополнительные сведения см. в разделе [как: изменение значения зарегистрировать](../debugger/how-to-edit-a-register-value.md).  
  
 Чтобы избежать загромождения, **регистрирует** окно объединены в группы, которые зависят от платформы и процессора типа. При желании группы можно отображать или скрывать. Дополнительные сведения см. в разделе [как: отображение и скрытие групп регистров](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Обобщенный Обзор в принципы использования регистров и окна регистров, см. в разделе [основы отладки: окно Регистры](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Отображение окна регистров  
  
-   На **Отладка** меню, выберите **Windows**, а затем выберите **регистрирует**.  
  
     Отладчик должен быть запущен либо находиться в режиме приостановки выполнения.  
  
    > [!NOTE]
    >  Для скриптов и приложений SQL сведения о регистрах недоступны.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)






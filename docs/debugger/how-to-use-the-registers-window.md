---
title: Просмотр значений регистров в отладчике Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257177"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Просмотр значений зарегистрировать и использовать окно Регистры в отладчике Visual Studio (C#, C++, Visual Basic, F#)
Окно "Регистры" доступно только в том случае, если включена отладка на уровне адреса в **параметры** диалоговом окне **Отладка** узел, **Общие** категории.  
  
 **Регистрирует** окне отображается содержимое регистров. Если вы храните **регистрирует** окно открыто при пошаговой отладке программы, вы увидите изменение значений регистров по ходу выполнения. Значения, которые недавно изменились, отображаются красным цветом. Значения регистров можно изменять. Дополнительные сведения см. в разделе [как: изменение значения зарегистрировать](../debugger/how-to-edit-a-register-value.md).  
  
 Чтобы избежать загромождения, **регистрирует** окно объединены в группы, которые зависят от платформы и процессора типа. При желании группы можно отображать или скрывать. Дополнительные сведения см. в разделе [как: отображение и скрытие групп регистров](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Обобщенный Обзор в принципы использования регистров и окна регистров, см. в разделе [основы отладки: окно Регистры](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Отображение окна регистров  
  
-   На **Отладка** меню, выберите **Windows**, а затем выберите **регистрирует** (или выберите **Ctrl** + **Alt**   +  **G**).  
  
     Отладчик должен быть запущен либо находиться в режиме приостановки выполнения.  
  
    > [!NOTE]
    >  Для скриптов и приложений SQL сведения о регистрах недоступны.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)
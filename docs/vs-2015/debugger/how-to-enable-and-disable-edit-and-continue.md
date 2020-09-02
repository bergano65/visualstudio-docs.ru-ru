---
title: Как включить и отключить функцию "изменить и продолжить" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689264"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Практическое руководство. Включение и выключение режима "Изменить и продолжить"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно отключить или включить функцию "изменить и продолжить" в диалоговом окне " **Параметры** " во время разработки. Этот параметр невозможно изменить в процессе отладки.  
  
 Операция "Изменить и продолжить" работает только в отладочных сборках. В случае машинного кода C++ для операции "Изменить и продолжить" требуется использовать параметр /INCREMENTAL.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Чтобы включить или отключить режим "Изменить и продолжить"  
  
1. Откройте страницу параметров отладки (**Сервис/параметры/Отладка**).  
  
2. Прокрутите вниз, чтобы **изменить категорию и продолжить** .  
  
3. Чтобы включить, установите флажок **включить изменение и продолжить** . Чтобы отключить, снимите флажок.  
  
   > [!NOTE]
   > Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в разделе [Настройка IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Нажмите кнопку **ОК**.  
  
   Дополнительные сведения об этих параметрах см. в разделе [Общие, отладка, диалоговое окно "Параметры"](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>См. также:  
 [Изменить и продолжить](../debugger/edit-and-continue.md)

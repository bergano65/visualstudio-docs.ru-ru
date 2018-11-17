---
title: 'Практическое: Включение и выключение изменить и продолжить | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5709b4bdae55c0ade6ca4559dcbaad8d66c0bbac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781261"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Практическое руководство. Включение и выключение режима "Изменить и продолжить"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно отключить или включить изменить и продолжить в **параметры** диалоговое окно во время разработки. Этот параметр невозможно изменить в процессе отладки.  
  
 Операция "Изменить и продолжить" работает только в отладочных сборках. В случае машинного кода C++ для операции "Изменить и продолжить" требуется использовать параметр /INCREMENTAL.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Чтобы включить или отключить режим "Изменить и продолжить"  
  
1. Откройте страницу параметров отладки (**Сервис / Параметры / Отладка**).  
  
2. Прокрутите вниз до раздела **изменить и продолжить** категории.  
  
3. Чтобы включить, установите **включить изменить и продолжить** "флажок". Чтобы отключить, снимите флажок.  
  
   > [!NOTE]
   >  Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в разделе [настроить IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Нажмите кнопку **ОК**.  
  
   Дополнительные сведения об этих параметрах см. в разделе [General, Debugging, диалоговое окно параметров](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>См. также  
 [Изменить и продолжить](../debugger/edit-and-continue.md)




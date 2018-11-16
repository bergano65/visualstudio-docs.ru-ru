---
title: Как определить, повреждают ли указатели адрес памяти? | Документы Майкрософт
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
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 013b88bcaa0d0cf9dc8ff308f43f3191ed2d0334
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734235"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Как определить, повреждают ли указатели адрес памяти?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Описание проблемы  
 Возможно, один из указателей повреждает память по адресу 0x00408000. Как определить, что происходит в этой точке?  
  
## <a name="solution"></a>Решение  
  
#### <a name="check-for-heap-corruption"></a>Проверка целостности кучи  
  
-   В большинстве случаев повреждение памяти происходит из-за повреждения кучи. Используйте программу глобальных флагов (gflags.exe) или pageheap.exe. См. в разделе [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Поиск места изменения адреса памяти  
  
1.  Задайте точку останова данных по адресу 0x00408000. См. в разделе [задайте точку останова изменений данных (только для машинного кода C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Когда будет достигнута точка останова, используйте **памяти** окно для просмотра памяти содержимое, начиная с адреса 0x00408000. Дополнительные сведения см. в разделе [памяти Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)




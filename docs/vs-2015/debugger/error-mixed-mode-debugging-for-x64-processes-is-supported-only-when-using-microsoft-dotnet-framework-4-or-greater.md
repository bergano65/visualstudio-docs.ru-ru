---
title: 'Ошибка: Смешанный режим отладки для x64 процессов поддерживается только в том случае, если с помощью Microsoft .NET Framework 4 или более поздней версии | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56ae0260b73d41e953fa25b74eae9b012604258a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106349"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Ошибка: Отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для отладки смеси управляемого и неуправляемого кода в 64-разрядном процессе необходимо использовать версию 4 платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Отладка в смешанном режиме для 64-разрядных процессов при использовании версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], предшествующих версии 4, не поддерживается.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Выполните одно из следующих действий.  
  
    - Обновите [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] до версии 4.  
  
    - Постройте для отладки 32-разрядную версию приложения.  
  
## <a name="see-also"></a>См. также  
 [Настройка инструментов удаленной отладки в устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)

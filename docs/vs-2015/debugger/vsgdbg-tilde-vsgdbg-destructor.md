---
title: 'VsgDbg:: ~ VsgDbg (деструктор) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990205"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Уничтожает экземпляр `VsgDbg` класса. Если активно идет запись графических данных, файл журнала графики является завершения и закрытия и освобождение ресурсов, которые были использованы при активный захват данных графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также  
 [VsgDbg::VsgDbg (конструктор)](../debugger/vsgdbg-vsgdbg-constructor.md)

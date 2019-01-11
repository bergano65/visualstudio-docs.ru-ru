---
title: 'VsgDbg:: ~ VsgDbg (деструктор) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d68b7dbf64f15b376cd49bdd2d60f507014f5167
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877865"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Уничтожает экземпляр `VsgDbg` класса. Если активно идет запись графических данных, файл журнала графики является завершения и закрытия и освобождение ресурсов, которые были использованы при активный захват данных графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также раздел  
 [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
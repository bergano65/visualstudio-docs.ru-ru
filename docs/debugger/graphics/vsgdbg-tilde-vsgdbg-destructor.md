---
title: 'VsgDbg:: ~ VsgDbg (деструктор) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8af808d635e6057c449d1fb0b055e8ad9caa9f11
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Удаляет экземпляр `VsgDbg` класса. Если активно записывается графические данные, завершает работу и закрытии файла журнала графики и освобождать ресурсы, которые были использованы при активно захват графической информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также  
 [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
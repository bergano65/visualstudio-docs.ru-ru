---
title: "VsgDbg:: ~ VsgDbg (деструктор) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8d34fc9ac09f944fea44baff3ceea4a121a8009
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Удаляет экземпляр `VsgDbg` класса. Если активно записывается графические данные, завершает работу и закрытии файла журнала графики и освобождать ресурсы, которые были использованы при активно захват графической информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также  
 [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
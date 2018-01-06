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
ms.workload: multiple
ms.openlocfilehash: 16fce161dc1c01797a67fe8d104c26ce603a4b76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Удаляет экземпляр `VsgDbg` класса. Если активно записывается графические данные, завершает работу и закрытии файла журнала графики и освобождать ресурсы, которые были использованы при активно захват графической информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также  
 [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
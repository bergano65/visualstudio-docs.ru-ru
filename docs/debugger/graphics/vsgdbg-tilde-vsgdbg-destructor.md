---
title: 'VsgDbg:: ~ VsgDbg (деструктор) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca62daa70602ac48e2b0871f764d0572b9da5f73
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Удаляет экземпляр `VsgDbg` класса. Если активно записывается графические данные, завершает работу и закрытии файла журнала графики и освобождать ресурсы, которые были использованы при активно захват графической информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также  
 [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
---
title: "CaptureCurrentFrame | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcdeee28077f2c7affd1c4cd1f82d8c8cb29494b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Захватывает оставшуюся часть текущего кадра в файл журнала графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Примечания  
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.  
  
 Для захвата кадра, необходимо подготовить приложение для сбора и записи данных графики — то есть, то необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>См. также  
 [Init](init.md)   
 [BeginCapture](begincapture.md)
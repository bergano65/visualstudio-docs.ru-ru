---
title: CaptureCurrentFrame | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978992"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Захватывает оставшуюся часть текущего кадра в файл журнала графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Примечания  
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.  
  
 Для захвата кадра необходимо подготовить приложение к захвату и записи данных графики — то есть вам необходимо вызвать метод [Init](../debugger/init.md) через экземпляр `VsgDbg` класса перед вызовом метода `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>См. также  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)

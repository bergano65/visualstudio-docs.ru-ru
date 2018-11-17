---
title: CaptureCurrentFrame | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76dca819f6a6a236f3b0e206dd0585cebce3f25e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764423"
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
 [init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)




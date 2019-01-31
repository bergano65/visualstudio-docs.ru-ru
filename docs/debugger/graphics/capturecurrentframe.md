---
title: CaptureCurrentFrame | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05d93e4cee3fb4969b928caa3ae76112708469f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997238"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Захватывает оставшуюся часть текущего кадра в файл журнала графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Примечания  
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.  
  
 Для захвата кадра необходимо подготовить приложение к захвату и записи данных графики — то есть вам необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>См. также раздел  
 [Init](init.md)   
 [BeginCapture](begincapture.md)
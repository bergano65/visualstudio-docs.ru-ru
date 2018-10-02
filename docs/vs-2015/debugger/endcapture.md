---
title: EndCapture | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 142a2f7b43f3b0a16d4dd1d983f11b485022f43f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570358"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [EndCapture](https://docs.microsoft.com/visualstudio/debugger/graphics/endcapture).  
  
Завершает интервал захвата, начатый функцией `BeginCapture`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Примечания  
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.  
  
 Для захвата интервала необходимо подготовить приложение к захвату и записи данных графики — то есть вам необходимо вызвать метод [Init](../debugger/init.md) через экземпляр `VsgDbg` класса перед вызовом метода `BeginCapture` или `EndCapture`.  
  
## <a name="see-also"></a>См. также  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)




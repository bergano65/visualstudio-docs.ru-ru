---
title: EndCapture | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3425561bc3d7db845733e7b6887c26f26c363df8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="endcapture"></a>EndCapture
Завершает интервал захвата, начатый функцией `BeginCapture`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Примечания  
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.  
  
 Записывать интервал, необходимо подготовить приложение для сбора и записи данных графики — то есть, то необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `BeginCapture` или `EndCapture`.  
  
## <a name="see-also"></a>См. также  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)
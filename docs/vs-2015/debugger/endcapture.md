---
title: EndCapture | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a451746cae978f141b30fb7295a82310e04367c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197098"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Завершает интервал захвата, начатый функцией `BeginCapture`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Примечания  
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.  
  
 Для захвата интервала необходимо подготовить приложение к захвату и записи данных графики, т. е. необходимо вызвать метод [Init](../debugger/init.md) посредством экземпляра класса `VsgDbg`, прежде чем вызывать `BeginCapture` или `EndCapture`.  
  
## <a name="see-also"></a>См. также:  
 [бегинкаптуре](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)

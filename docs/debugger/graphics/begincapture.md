---
title: BeginCapture | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c04f199472afc516304f7a8f4f135174593b60
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473619"
---
# <a name="begincapture"></a>BeginCapture
Начинается интервал захвата, будут заканчиваться `EndCapture`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Примечания  
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.  
  
 Записывать интервал, необходимо подготовить приложение для сбора и записи данных графики — то есть, то необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `BeginCapture` или `EndCapture`.  
  
## <a name="see-also"></a>См. также  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)
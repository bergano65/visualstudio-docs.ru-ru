---
title: "Вариант размера окна просмотра 1 x 1 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ab9f8be1d202f21147afaf9f4f52a3c90c403ed8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="1x1-viewport-size-variant"></a>Вариант размера окна просмотра (1x1)
Размеры окна просмотра для всех целевых объектов отрисовки уменьшаются до 1 x 1 пикселей.  
  
## <a name="interpretation"></a>Интерпретация  
 Уменьшение окна просмотра снижает число пикселей, требующих затенения, но не снижает число вершин, которое необходимо обработать. Уменьшение размеров окна просмотра до 1 x 1 пикселя приводит к тому, что затенение пикселей в приложении не используется.  
  
 Если этот вариант дает значительный прирост производительности, это может указывать на то, что скорость заполнения в приложении слишком высока. Это может означать, что вы выбрали слишком высокое разрешение для целевой платформы или что приложение тратит много времени на затенение пикселей, которые затем перезаписываются (перекрываются). Этот результат подразумевает, что уменьшение размера буфера кадров или числа операций перекрытия может повысить производительность приложения.  
  
## <a name="remarks"></a>Примечания  
 Размеры окна просмотра устанавливаются равными 1 x 1 пиксель после каждого вызова метода `ID3D11DeviceContext::OMSetRenderTargets` или `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Пример  
 Этот вариант можно воспроизвести с помощью следующего кода:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
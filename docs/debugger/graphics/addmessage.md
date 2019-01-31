---
title: AddMessage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aa23265c2f0d8d006d53faf575e2ea608c071d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027533"
---
# <a name="addmessage"></a>AddMessage
Добавляет пользовательское сообщение на головной дисплей (*HUD*) диагностики графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `szMessage`  
 Сообщение, добавляемое на HUD.  
  
## <a name="remarks"></a>Примечания  
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. На нем отображаются сведения о приложении во время выполнения и о захвате данных графики, а также сообщения, добавленные путем вызова этой функции.  
  
 Чтобы добавить сообщение на HUD, необязательно вести активный захват данных графики: сообщение можно добавить посредством экземпляра класса `VsgDbg`, но без предварительного вызова функции-члена [Init](init.md). Сообщения только отображаются на HUD; в файл журнала графики они не записываются.
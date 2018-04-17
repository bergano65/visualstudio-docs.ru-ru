---
title: AddMessage | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f58f716aca83cce9f2e04129d45a9cf9c97df50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="addmessage"></a>AddMessage
Добавляет пользовательское сообщение диагностики графики *HUD* (головной дисплей).  
  
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
  
 Добавление сообщения на hud, не нужно активно захват графических данных — то есть сообщения могут быть добавлены в экземпляр `VsgDbg` класса, но [Init](init.md) не предназначена для сначала вызвать функцию-член. Сообщения только отображаются на HUD; в файл журнала графики они не записываются.
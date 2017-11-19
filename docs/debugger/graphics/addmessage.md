---
title: "AddMessage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0050f5022b31020879b45e45da48546e5a7caa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
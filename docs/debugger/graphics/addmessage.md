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
ms.workload: multiple
ms.openlocfilehash: 0841e622b0fe7c0d01d374da21a12a151c59021d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
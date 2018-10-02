---
title: IDiaSession::put_loadAddress | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e39ac68468113f371c032f2f29b4613fa229a3b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560353"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSession::put_loadAddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-put-loadaddress).  
  
Задает адрес загрузки исполняемого файла, соответствующее к символам в данном хранилище символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `NewVal`  
 [in] Загрузить адрес для исполняемого файла.  
  
## <a name="remarks"></a>Примечания  
 Свойства символа виртуальный адрес (VA) вычисляются с помощью значения этого метода. Если это свойство не задано значение ненулевое, виртуальных адресов не вычисляются.  
  
> [!NOTE]
>  Этот метод необходимо вызвать при получении [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объекта и перед началом работы с помощью объекта, если необходимо использовать все виртуальные свойства на символы.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)




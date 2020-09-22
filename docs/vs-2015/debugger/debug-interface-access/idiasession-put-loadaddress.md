---
title: IDiaSession::p ut_loadAddress | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842336"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `NewVal`  
 окне Загружается адрес исполняемого файла.  
  
## <a name="remarks"></a>Remarks  
 Свойства виртуального адреса символа (ва) вычисляются с помощью значения этого метода. Виртуальные адреса не вычисляются, если это свойство не имеет значение, отличное от нуля.  
  
> [!NOTE]
> Этот метод следует вызывать при получении объекта [IDiaSession](../../debugger/debug-interface-access/idiasession.md) и перед началом использования объекта, если необходимо использовать виртуальные свойства в символах.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)

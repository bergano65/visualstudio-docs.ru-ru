---
title: IDiaSession::put_loadAddress | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0b04db800e5b61ef1598fe4c81a9ab362e375e3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462650"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Задает адрес загрузки для исполняемого файла, соответствующее для символов в данном хранилище символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `NewVal`  
 [in] Загрузить адрес для исполняемого файла.  
  
## <a name="remarks"></a>Примечания  
 Свойства виртуального адреса (VA) символа вычисляются с помощью значения этого метода. Если это свойство не задано равным нулю, виртуальных адресов не вычисляются.  
  
> [!NOTE]
>  Необходимо вызвать этот метод при получении [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объекта и перед началом работы с помощью объекта, если необходимо использовать любые виртуальные свойства на символы.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
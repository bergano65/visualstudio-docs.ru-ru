---
title: IDiaEnumSourceFiles::Clone | Документация Майкрософт
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
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d56f2a841056c0b8f924f5f47ea3479997cccab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559643"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaEnumSourceFiles::Clone](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsourcefiles-clone).  
  
Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSourceFiles** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppenum  
 [out] Возвращает [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , содержащий копию перечислителя. Источник, который файлы не дублируются, только перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)




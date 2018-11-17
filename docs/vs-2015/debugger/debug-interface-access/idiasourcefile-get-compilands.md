---
title: IDiaSourceFile::get_compilands | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 813eff61f44480207fd6244040c478fbed9b766f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806871"
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечислитель единиц компиляции, номера строки, ссылающиеся на этот файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppRetVal`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список всех компилируемых объектах, которые имеют номера строк, ссылающихся на этот файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)




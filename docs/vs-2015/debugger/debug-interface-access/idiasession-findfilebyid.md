---
title: IDiaSession::findFileById | Документация Майкрософт
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
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e54267e86854098e263c74a9d0e7042540e02025
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569203"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSession::findFileById](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findfilebyid).  
  
Извлекает исходный файл, идентификатор файла источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uniqueId`  
 [in] Задает идентификатор исходного файла.  
  
 `ppResult`  
 [out] Возвращает [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) извлечь объект, представляющий исходный файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор файла источника — это уникальное значение, используется внутренним образом для пакета SDK для доступа к интерфейсу отладки, чтобы сделать уникальным все исходные файлы. Этот метод обычно используется внутренне для пакета SDK для доступа к интерфейсу отладки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)




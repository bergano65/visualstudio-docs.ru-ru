---
title: IDiaSession::findInlineeLinesByAddr | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b35850367ef4bcc4e49cc3d6e76b41a2e9f4cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151704"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном диапазоне адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 окне `IDiaSymbol` Объект, представляющий родительский элемент.  
  
 `isect`  
 окне Указывает компонент раздела адреса.  
  
 `offset`  
 окне Указывает компонент смещения адреса.  
  
 `length`  
 окне Указывает диапазон адресов (в байтах), который охватывает этот запрос.  
  
 `ppResult`  
 заполняет Содержит `IDiaEnumLineNumbers` объект, содержащий список извлекаемых номеров строк.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Симтаженум](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

---
title: IDiaDataSource::openSession | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198605"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает сеанс для выполнения запросов к символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppSession  
 [out] Возвращает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объект, представляющий открытый сеанс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) объекта не ранее был инициализирован с источником символов.|  
|E_INVALIDARG|Недопустимый параметр `ppSession`.|  
|E_OUTOFMEMORY|Недостаточно памяти для открытия сеанса.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод открывает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объекта для источника данных.  
  
 `IDiaSession` объекты реализацию запросов в источник данных. Сеанс управляет одно адресное пространство для каждого набора символов отладки. Если файл .exe или .dll, описываемый символы источника данных активное участие в нескольких адресов диапазонов (например, так как несколько процессов будет загружен), то следует использовать один сеанс для каждого диапазона адресов.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

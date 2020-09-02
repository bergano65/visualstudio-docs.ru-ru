---
title: 'Идиадатасаурце:: Лоаддатафромистреам | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547459"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подготавливает данные отладки, хранящиеся в файле базы данных программы (. pdb), к которому осуществляется доступ через поток данных в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 пистреам  
 окне <xref:IStream> Объект, представляющий используемый поток данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_FORMAT|Попытка доступа к файлу с устаревшим форматом.|  
|E_INVALIDARG|Недопустимый параметр.|  
|E_UNEXPECTED|Источник данных уже подготовлен.|  
  
## <a name="remarks"></a>Remarks  
 Этот метод позволяет получать данные отладки для исполняемого файла из памяти через <xref:IStream> объект.  
  
 Чтобы загрузить PDB-файл без проверки, используйте метод [идиадатасаурце:: лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Чтобы проверить PDB-файл на соответствие конкретным критериям, используйте метод [идиадатасаурце:: лоадандвалидатедатафромпдб](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Чтобы получить доступ к процессу загрузки данных (посредством механизма обратного вызова), используйте метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Идиадатасаурце:: Лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)

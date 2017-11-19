---
title: "IDiaDataSource::loadDataFromIStream | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6db2e9fb90104de121faafc2efa90fdaf52da47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Подготавливает отладочные данные, хранящиеся в PDB-файл программы, доступных через поток данных в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pIStream  
 [in] <xref:IStream> Объект, представляющий поток данных для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_FORMAT|Предпринята попытка доступа к файлу с устаревший формат.|  
|E_INVALIDARG|Invalidparameter.|  
|E_UNEXPECTED|Источник данных уже был подготовлен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет данные отладки для исполняемого файла может быть получена из памяти посредством <xref:IStream> объекта.  
  
 Чтобы загрузить PDB-файла без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.  
  
 Чтобы проверить файл PDB-файл на соответствие определенным критериям, используйте [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) метод.  
  
 Чтобы получить доступ к процесс загрузки данных (через механизм обратного вызова), используйте [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
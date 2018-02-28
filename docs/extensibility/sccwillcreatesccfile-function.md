---
title: "Функция SccWillCreateSccFile | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6a0344177d50d7121b1116e80983db80233dac90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccwillcreatesccfile-function"></a>Функция SccWillCreateSccFile
Эта функция определяет, поддерживает ли подключаемый модуль системы управления версиями Создание MSSCCPRJ. Файл SCC для каждого заданного файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Число имен файлов, включенных в `lpFileNames` массива, а также длину `pbSccFiles` массива.  
  
 lpFileNames  
 [in] Массив полных имен для проверки (массива должен быть выделен вызывающим объектом).  
  
 pbSccFiles  
 [in, out] Массив, в котором сохраняются результаты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Выполнено.|  
|SCC_E_INVALIDFILEPATH|Один из путей в массиве является недопустимым.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция вызывается со списком файлов, чтобы определить, если подключаемый модуль системы управления версиями обеспечивает поддержку в MSSCCPRJ. Файл SCC для каждого заданного файла (Подробнее о MSSCCPRJ. Файл SCC разделе [MSSCCPRJ. Файл SCC](../extensibility/mssccprj-scc-file.md)). Подключаемые модули управления версиями можно объявить, имеют ли они возможность создания MSSCCPRJ. Файлы SCC, объявив `SCC_CAP_SCCFILE` во время инициализации. Подключаемый модуль возвращает `TRUE` или `FALSE` каждого файла в `pbSccFiles` массива, указывающая, какой из заданного файлы MSSCCPRJ. Поддержка SCC. Если подключаемый модуль возвращает успех код из функции, соблюдаются значения в возвращаемый массив. В случае сбоя массива учитывается.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
---
title: "Коды ошибок | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50d05e529a3202f59df53801728b40fee1c68f40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-codes"></a>Коды ошибок
При API подключаемых модулей для управления источника функция возвращает ошибку, он ожидается один из следующих кодов ошибки. Все ошибки отрицательное значение, предупреждения или информационные коды являются положительными, и 0 — успех.  
  
|Код ошибки|Значение|Описание|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Подключаемый модуль поддерживает добавление файлов из системы управления версиями в два этапа. Дополнительные сведения см. в разделе [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Имя локального файла отличается от файла в базе данных управления версиями (например, [SccDiff](../extensibility/sccdiff-function.md) могут возвращать это значение).|  
|`SCC_I_RELOADFILE`|5|Локальный файл был изменен во время операция системы управления версиями; интегрированной среды разработки следует перезагрузить файл, если это возможно.|  
|`SCC_I_FILENOTAFFECTED`|4|Файл не влияет.|  
|`SCC_I_PROJECTCREATED`|3|Проект был создан во время операции системы управления версиями (например, во время вызова [SccOpenProject](../extensibility/sccopenproject-function.md) при `SCC_OP_CREATEIFNEW` установлен флаг).|  
|`SCC_I_OPERATIONCANCELED`|2|Операция была отменена.|  
|`SCC_I_ADV_SUPPORT`|1|Подключаемый модуль поддерживает дополнительные параметры для заданной команды. Дополнительные сведения см. в разделе [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Выполнено.|  
|`SCC_E_INITIALIZEFAILED`|-1|Ошибка: Сбой при инициализации.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Ошибка: неизвестный проект.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Ошибка: не удается создать проект.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Ошибка: файл не извлечен.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Ошибка: файл уже извлечен.|  
|`SCC_E_FILEISLOCKED`|-6|Ошибка: файл заблокирован.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Ошибка: файл имеет монопольно.|  
|`SCC_E_ACCESSFAILURE`|-8|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|`SCC_E_CHECKINCONFLICT`|-9|Ошибка: произошел конфликт во время возврата.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Ошибка: файл уже существует.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Ошибка: файл не находится в системе управления версиями.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Ошибка: файл извлечен.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Ошибка: отсутствует версия без указанного.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Ошибка: операция не поддерживается.|  
|`SCC_E_NONSPECIFICERROR`|-15|Обнаружена неспецифическая ошибка.|  
|`SCC_E_OPNOTPERFORMED`|-16|Ошибка, операция не выполнена.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Ошибка: тип файла, например, двоичных данных, не поддерживается системы управления исходным кодом.|  
|`SCC_E_VERIFYMERGE`|-18|Файл был автоматическое слияние, но не была выполнена проверка, так как он является проверка ожидающих пользователя.|  
|`SCC_E_FIXMERGE`|-19|Файл был автоматического слияния, но еще не возвращен из-за конфликта слияния, который необходимо разрешить вручную.|  
|`SCC_E_SHELLFAILURE`|-20|Ошибка из-за сбоя оболочки.|  
|`SCC_E_INVALIDUSER`|-21|Ошибка: недопустимый пользователь.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Ошибка: уже открыт проект.|  
|`SCC_E_PROJSYNTAXERR`|-23|Синтаксическая ошибка проекта.|  
|`SCC_E_INVALIDFILEPATH`|-24|Ошибка: недопустимый путь к файлу.|  
|`SCC_E_PROJNOTOPEN`|-25|Ошибка: проект не открыт.|  
|`SCC_E_NOTAUTHORIZED`|-26|Ошибка: пользователь не авторизован для выполнения этой операции.|  
|`SCC_E_FILESYNTAXERR`|-27|Синтаксическая ошибка файла.|  
|`SCC_E_FILENOTEXIST`|-28|Ошибка, локальный файл не существует.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Ошибка: произошла ошибка подключения.|  
|`SCC_E_UNKNOWNERROR`|-30|Произошла неизвестная ошибка.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Сейчас выполняется фоновая операция get.|  
  
## <a name="macros-provided-for-quick-checking"></a>Макросы для Быстрая проверка  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Примечания  
 Все функции API подключаемых модулей для управления источника (за исключением [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), и [SccDiff](../extensibility/sccdiff-function.md)) которых ожидается успешное выполнение после локальных файлов, которые передаются как аргументы, как не существует в рабочей папке. Например, интегрированной среды разработки может выдавать вызов [SccCheckout](../extensibility/scccheckout-function.md) или [SccUncheckout](../extensibility/sccuncheckout-function.md) для файла, который не существует в рабочей папке, но существует в системе управления версиями. Этот вызов пройдет успешно. Только в том случае, если файл отсутствует в рабочую папку или в системе управления версиями функция ожидается сбой.  
  
 Некоторые функции, например `SccAdd` и `SccCheckin`, в частности должен возвращать `SCC_E_FILENOTEXIST` при файл в рабочей папке не существует. Другие функции, должны успешно при работе файл не существует, если функции работают на допустимое имя файла в системе управления версиями.  
  
 Подключаемый модуль системы управления версиями следует делать никаких предположений о правах доступа для файла в рабочей папке, даже если подключаемый модуль пометили файл только для чтения во время некоторой операции. Файл в рабочей папке можно переместить, удаленные и изменения вне подключаемые в элемент управления.  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
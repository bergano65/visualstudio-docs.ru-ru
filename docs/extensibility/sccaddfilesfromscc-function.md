---
title: Функция SccaddFilesFromSCC (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701289"
---
# <a name="sccaddfilesfromscc-function"></a>Функция SccaddFilesFromSCC
Эта функция добавляет список файлов от управления исходным ресурсом к открываемому в настоящее время проекту.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 lpUser

(в, вне) Имя пользователя (до SCC_USER_SIZE, включая терминатор null).

 lpAuxProjPath

(в, вне) Вспомогательная строка, определяющая `SCC_PRJPATH_`проект (вплоть до СИЗЕ, включая нулевой терминатор).

 cФайлы

(в) Количество файлов, `lpFilePaths`предоставленных .

 lpFilePaths

(в, вне) Массив имен файлов для добавления в текущий проект.

 lpНаправление

(в) Путь назначения, по которому должны быть написаны файлы.

 lpКомментарий

(в) Комментарий, который будет применяться к каждому из добавленных файлов.

 pbРезультаты

(в, вне) Массив флагов, которые должны указывать на успех (ненулевой или true) или сбой (ноль или FALSE) для каждого файла (размер массива должен быть по крайней мере `cFiles` длинным).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Проект не открыт.|
|SCC_E_OPNOTPERFORMED|Подключение не является тем же проектом, указанным`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Пользователь не уполномочен обновлять базу данных.|
|SCC_E_NONSPECIFICERROR|Неизвестная ошибка.|
|SCC_I_RELOADFILE|Файл или проект необходимо перезагрузить.|

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)

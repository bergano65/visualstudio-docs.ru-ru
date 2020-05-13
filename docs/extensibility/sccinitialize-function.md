---
title: Функция SccInitialize (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700632"
---
# <a name="sccinitialize-function"></a>Функция SccInitialize
Эта функция инициализирует плагин управления исходным управлением и предоставляет возможности и ограничения интегрированной среде разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Параметры
 `ppvContext`

(в) Плагин управления исходным элементом может поместить указатель на структуру контекста здесь.

 `hWnd`

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 `lpCallerName`

(в) Название программы, вызывающей плагин управления исходным элементом.

 `lpSccName`

(в, вне) Буфер, где плагин управления исходным источником ставит `SCC_NAME_LEN`свое собственное имя (не превышать).

 `lpSccCaps`

(ваут) Возвращает флаги возможностей управления исходным элементом.

 `lpAuxPathLabel`

(в, вне) Буфер, где плагин управления исходным кодом `lpAuxProjPath` ставит строку, которая описывает параметр, возвращенный [SccOpenProject](../extensibility/sccopenproject-function.md) и [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (не превышать). `SCC_AUXLABEL_LEN`

 `pnCheckoutCommentLen`

(ваут) Возвращает максимальную допустимую длину для выездного комментария.

 `pnCommentLen`

(ваут) Возвращает максимальную допустимую длину для других комментариев.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Инициализация управления исходом увенчалась успехом.|
|SCC_E_INITIALIZEFAILED|Невозможно инициализовать систему.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять указанную операцию.|
|SCC_E_NONSPECFICERROR|Неспецифический сбой; система управления источниками не была инициализирована.|

## <a name="remarks"></a>Примечания
 IDE вызывает эту функцию при первой загрузке плагина управления исходным управлением. Это позволяет IDE передавать определенную информацию, такую как имя вызываемого абонента, плагину. IDE также получает обратно определенную информацию, такую как максимально допустимая длина для комментариев и возможности плагина.

 Указывает `ppvContext` на `NULL` указатель. Плагин управления исходным элементом может выделить структуру для собственного `ppvContext`использования и хранить указатель на эту структуру в . IDE передаст этот указатель любой другой функции VSSCI API, что позволит плагину иметь контекстную информацию, не прибегая к глобальному хранению и поддерживать несколько экземпляров плагина. Эта структура должна быть разослана, когда [SccUninitialize](../extensibility/sccuninitialize-function.md) называется.

 Параметры `lpCallerName` `lpSccName` и параметры позволяют iDE и плагину управления исходным источником обмениваться именами. Эти имена могут быть использованы просто для различения между несколькими экземплярами, или они могут фактически отображаться в меню или диалоговых коробках.

 Параметр `lpAuxPathLabel` представляет собой строку, используемую в качестве комментария для определения вспомогательного пути проекта, который хранится в файле решения и передается плагину управления исходным кодом в вызове [в SccOpenProject.](../extensibility/sccopenproject-function.md) [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]использует строку "SourceSafe Project:"; другие плагины управления исходным управлением должны воздерживаться от использования данной строки.

 Параметр `lpSccCaps` дает плагин управления исходным элементом место для хранения bitflags с указанием возможностей плагина. (Для полного списка возможностей bitflags, см [Возможности флаги](../extensibility/capability-flags.md)). Например, если плагин планирует записать результаты в функцию обратного вызова, плагин установит бит возможности SCC_CAP_TEXTOUT. Это будет сигналом IDE для создания окна для результатов управления версиями.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Флаги возможностей](../extensibility/capability-flags.md)

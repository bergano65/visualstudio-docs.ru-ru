---
title: Настройка отображения окна инструментов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 175e2005047312f6815e90c21c60ab831c036064
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tool-window-display-configuration"></a>Настройка отображения окна инструментов
Когда VSPackage регистрирует окна инструментов, положение по умолчанию, размер, стиль закрепления и другие сведения о видимости указывается в необязательных значений. Дополнительные сведения о регистрации окна инструментов см. в разделе [окна инструментов в реестре](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Сведения об отображении окна  
 Настройка основного экрана окно инструментов хранится в до шести необязательные значения:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|name|REG_SZ|«Краткое имя здесь»|Краткое имя, описывающее окна инструментов. Используется только для справки в реестре.|  
|Float|REG_SZ|«X1, Y1, X2, Y2»|Четыре значения с разделителями-запятыми. X1, Y1 — это координата левого верхнего угла окна инструментов. X2, Y2 — это координата нижнего правого угла. Все значения — в экранных координатах.|  
|Стиль|REG_SZ|«MDI»<br /><br /> «Float»<br /><br /> «Связанные»<br /><br /> «С вкладками»<br /><br /> «AlwaysFloat»|Ключевое слово, указав первоначального отображения состояния окна инструментов.<br /><br /> «MDI» = прикреплено к окно MDI-приложения.<br /><br /> «Float» = с плавающей запятой.<br /><br /> «Связанные» = связан с другим окном (указанный в запись в окне).<br /><br /> «С вкладками» = в сочетании с другой окно инструментов.<br /><br /> «AlwaysFloat» = не может быть закреплено.<br /><br /> Дополнительные сведения см. ниже в разделе комментариев.|  
|Окно|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID для окна, к которому могут быть связаны или с вкладками в окне инструментов. Идентификатор GUID могут входить в один из собственных windows или одно из окон в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.|  
|Ориентация|REG_SZ|«Левый»<br /><br /> «Right»<br /><br /> «Top»<br /><br /> «Снизу»|См. примечания ниже.|  
|DontForceCreate|REG_DWORD|0 или 1|Если его значение не равно нулю, а эта запись отсутствует, окно загружен, но не сразу отображаться.|  
  
### <a name="comments"></a>Комментарии  
 Запись Ориентация определяет позицию, где закрепляет окно инструментов при двойном щелчке на заголовке окна. Позиция задается относительно окна, указанную в запись в окне. Если запись стиля имеет значение «Связанный», ориентация запись может быть «Left», «Right», «Top» или «Bottom». Если операция стиль «Вкладки», ориентацию запись можно «оставить» или «Правой» и указывает, где эта вкладка добавляется. Если запись стиля «Float», сначала располагается окно инструмента. При двойном щелчке в заголовке применяются операции ориентацию и окна, и в окне используется стиль «Вкладки». Если операция стиль «AlwaysFloat», нельзя закрепить окно инструментов. Если запись стиля «MDI», окно инструментов связана области MDI, и запись в окне игнорируется.  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Отображение окна инструментов  
 Значения в подраздел видимость необязательно определяют параметры видимости окно инструментов. Имена значений используются для хранения идентификаторов GUID, для команд, требующих Отображение окна. Если команда выполняется, интегрированной среды разработки гарантирует, что создан и доступны в окне инструментов.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Нет|Оставьте пустым.|  
|*\<ИДЕНТИФИКАТОР GUID &GT;*|REG_DWORD или REG_SZ|0 или описательная строка.|Необязательный. Имя входа должно быть GUID команды, требующие видимость. Значение содержит только строку подробное сообщение. Как правило, является значение `reg_dword` равно 0.|  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
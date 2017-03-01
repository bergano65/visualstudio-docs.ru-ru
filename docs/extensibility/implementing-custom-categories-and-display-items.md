---
title: "Реализация пользовательских категорий и отображаемые элементы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>Реализация пользовательских категорий и отображения элементов
Можно предоставить VSPackage управления шрифты и цвета текста для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) через пользовательские категории и отображаемые элементы.  
  
 Пользовательские категории и отображать элементы находятся на **шрифты и цвета** страницу свойств. Чтобы открыть **шрифты и цвета** свойство страницы **средства** меню, щелкните **параметры**. Разверните **среды** и нажмите кнопку **шрифты и цвета**.  
  
 При использовании этого механизма, необходимо реализовать VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>интерфейса и его связанных интерфейсов.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 В принципе, этот механизм может использоваться для изменения всех существующих **отображения элементов** и **категории** , содержащие их. Тем не менее, он должен не использоваться для изменения **EditorCategory текст** или его **отображения элементов**. Дополнительные сведения см. в разделе [шрифт и цвет Обзор](../extensibility/font-and-color-overview.md).  
  
 Чтобы реализовать пользовательскую **категории** или **отображения элементов**, VSPackage необходимо:  
  
-   Создайте или определите категории в реестре.  
  
     Реализация IDE **шрифты и цвета** страница свойств использует эти сведения для запроса к службе, поддерживающей данной категории правильно.  
  
-   Создайте или определите группы (необязательно) в реестре.  
  
     Его можно использовать для определения группы, который представляет объединение двух или более категорий. Если определена группа, интегрированной среды разработки автоматически объединяет подкатегории и распространяет отображаемые элементы в пределах группы.  
  
-   Реализация поддержки IDE.  
  
-   Обрабатывать изменения цвета и шрифта.  
  
 Сведения см. в разделе [параметров доступа к хранятся шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Для создания и определения категорий  
  
-   Создать специальный тип категории записи реестра в разделе [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio настроек*\FontAndColors\\`<Category>`]  
  
     *\<Категории настроек* нелокализованное имя категории.  
  
-   Добавить в реестр с двумя значениями:  
  
    |Имя|Тип|Данные|Описание|  
    |----------|----------|----------|-----------------|  
    |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для определения категории.|  
    |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы VSPackage, которая поддерживает категории.|  
  
 Службы, указанные в реестре должен предоставить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>в соответствующей категории.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
## <a name="to-create-or-identify-groups"></a>Для создания и определения групп  
  
-   Создать специальный тип категории записи реестра в разделе [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio настроек*\FontAndColors\\*\<группы настроек*]  
  
     *\<Группа настроек* нелокализованное имя группы.  
  
-   Добавить в реестр с двумя значениями:  
  
    |Имя|Тип|Данные|Описание|  
    |----------|----------|----------|-----------------|  
    |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для определения группы.|  
    |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы, которая поддерживает категории.|  
  
 Службы, указанные в реестре должны предоставлять реализацию метода `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` для соответствующей группы.  
  
## <a name="to-implement-ide-support"></a>Для реализации поддержки интегрированной среды разработки  
  
-   Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, который возвращает либо <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>интерфейс или `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` интерфейса интегрированной среды разработки для каждого **категории** или кодом GUID группы.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>  
  
-   Для каждого **категории** его поддерживает, VSPackage реализует отдельный экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
-   Методы реализуется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>необходимо предоставить интегрированная среда разработки с:</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Списки **отображения элементов** в **категории.**  
  
    -   Имена локализуемых для **отображения элементов**.  
  
    -   Отобразить сведения для каждого члена **категории**.  
  
    > [!NOTE]
    >  Каждый **категории** должен содержать по крайней мере один **отображаемым элементом**.  
  
-   Интегрированная среда разработки использует `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` интерфейс, чтобы определить объединение несколько категорий.  
  
     Его реализация предоставляет интегрированную среду разработки с:  
  
    -   Список **категории** , относятся к данной группе.  
  
    -   Доступ к экземплярам <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>поддержки каждого **категории** в пределах группы.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Имена локализуемых группы.  
  
-   Обновление интегрированной среды разработки:  
  
     IDE кэширует сведения о **шрифт и цвет** параметры. Таким образом, после внесения изменений интегрированной среды разработки **шрифт и цвет** конфигурации, целесообразно убедитесь в том, что кэш не требует обновления.  
  
 Обновление кэша выполняется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>интерфейс и может быть выполнено глобально или только на выбранные элементы.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="to-handle-font-and-color-changes"></a>Для обработки шрифт и цвет изменяется.  
 Для правильной поддержки Раскраска текста, отображаемого в VSPackage, выделение цветом служба, поддерживающая VSPackage необходимо реагировать на инициированная пользователем изменения через **шрифты и цвета** страница свойств. VSPackage достигается за счет:  
  
-   Обработка события, вызываемые в интегрированной среде разработки, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     IDE вызывает соответствующий метод после изменения пользователя **шрифты и цвета** страницы. Например, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>метода, если выбран новый шрифт.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>  
  
     -или-  
  
-   Опрос Интегрированной среде разработки для изменения.  
  
     Это можно сделать с помощью реализовать систему <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Хотя в основном для поддержки сохраняемости, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>метод может использоваться для получения сведений шрифт и цвет для **отображения элементов**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Дополнительные сведения см. в разделе [параметров доступа к хранятся шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Чтобы обеспечить правильность результатов, полученных с помощью опросов, часто бывает полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>интерфейс, чтобы определить необходимость сброса кэша и обновление до вызова методов извлечения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Получение шрифта и цвет шрифта для текста цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Доступ к хранимой шрифта и цветов](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Практическое руководство: доступ к встроенных шрифтов и цветовой схемы](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Обзор цвета и шрифта](../extensibility/font-and-color-overview.md)

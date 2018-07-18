---
title: Реализация пользовательских категорий и отображаемые элементы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9593a7addcd9a3f100f45f69e7e692c396e33bfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134887"
---
# <a name="implementing-custom-categories-and-display-items"></a>Реализация пользовательских категорий и отображаемые элементы
VSPackage может предоставить управления шрифты и цвета текста для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) через пользовательские категории и отображаемые элементы.

 Пользовательские категории и отображаемые элементы находятся на **шрифты и цвета** страницу свойств. Чтобы открыть **шрифты и цвета** свойства страницы на **средства** меню, нажмите кнопку **параметры**. Разверните **среды** и нажмите кнопку **шрифты и цвета**.

 При использовании этого механизма, пакеты VSPackage должны реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейса и его связанных интерфейсов.

 В принципе, этот механизм может использоваться для изменения все существующие **отображения элементов** и **категории** , содержащие их. Тем не менее, он должен не использоваться для изменения **EditorCategory текст** или его **отображения элементов**. Дополнительные сведения см. в разделе [шрифт и цвет Обзор](../extensibility/font-and-color-overview.md).

 Чтобы реализовать пользовательскую **категории** или **отображения элементов**, пакет VSPackage должен:

-   Создайте или определите категории в реестре.

     Реализация IDE **шрифты и цвета** страница свойств использует эти сведения для запроса правильно для службы, поддерживающей данной категории.

-   Создайте или определите группы (необязательно) в реестре.

     Его можно использовать для определения группы, представляющий объединение двух или более категорий. При определении группы, интегрированной среды разработки автоматически выполняет слияние подкатегории и распространяет отображаемые элементы в пределах группы.

-   Реализация поддержки IDE.

-   Обрабатывать изменения цвета и шрифта.

 Сведения см. в разделе [параметров доступа к хранимых шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Для создания и определения категорий

-   Создать специальный тип категории запись реестра [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >* \FontAndColors\\`<Category>`]

     *\<Категория >* нелокализованное имя категории.

-   Добавить в реестр с двумя значениями:

    |name|Тип|Данные|Описание|
    |----------|----------|----------|-----------------|
    |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для определения категории.|
    |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID пакета VSPackage службы, которая поддерживает категории.|

 Службы, указанный в разделе реестра необходимо обеспечить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> для соответствующей категории.

## <a name="to-create-or-identify-groups"></a>Для создания и определения групп

-   Создать специальный тип категории запись реестра [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >* \FontAndColors\\  *\<группы >*]

     *\<Группа >* нелокализованное имя группы.

-   Добавить в реестр с двумя значениями:

    |name|Тип|Данные|Описание|
    |----------|----------|----------|-----------------|
    |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для определения группы.|
    |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы, которая поддерживает категории.|

 Службы, указанный в разделе реестра необходимо обеспечить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> для соответствующей группы.

## <a name="to-implement-ide-support"></a>Чтобы обеспечить поддержку интегрированной среды разработки

-   Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, возвращающий либо <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейса или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс IDE для каждой **категории** или группе кодом GUID.

-   Для каждого **категории** его поддерживает, VSPackage реализует отдельный экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейса.

-   Методы реализуется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> необходимо предоставить среду IDE:

    -   Списки **отображения элементов** в **категории.**

    -   Локализуемые имен для **отображения элементов**.

    -   Отображение сведений о каждом члене **категории**.

    > [!NOTE]
    >  Каждый **категории** должен содержать по крайней мере один **отображаемым элементом**.

-   Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, чтобы определить объединение несколько категорий.

     Его реализация предоставляет интегрированную среду разработки с помощью:

    -   Список **категории** , относятся к данной группе.

    -   Доступ к экземплярам <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> поддержки каждого **категории** в пределах группы.

    -   Имена групп локализации.

-   Обновление интегрированной среды разработки:

     IDE кэширует сведения о **шрифт и цвет** параметры. Таким образом, после внесения изменений интегрированной среды разработки **шрифт и цвет** конфигурации, то желательно убедитесь в том, что кэш является актуальной.

 Обновление кэша выполняется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, а также может быть выполнено глобально или только на выбранные элементы.

## <a name="to-handle-font-and-color-changes"></a>Для обработки шрифт и цвет изменяется.
 Для правильной поддержки выделение цветом текста, который отображает VSPackage, выделение цветом служба, поддерживающая VSPackage должен отвечать на инициированной пользователем изменения, внесенные через **шрифты и цвета** страница «свойства». VSPackage делает это:

-   Обработка события, вызываемые IDE путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> интерфейса.

     IDE вызывает соответствующий метод после изменения пользователем **шрифты и цвета** страницы. Например, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> метод, если выбран новый шрифт.

     - или -

-   Опрос интегрированную среду разработки для изменения.

     Это можно сделать с помощью реализовать систему <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса. Несмотря на то что в основном для поддержки сохраняемости, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> метод может использоваться для получения данных шрифта и цвета для **отображения элементов**. Дополнительные сведения см. в разделе [параметров доступа к хранимых шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Чтобы обеспечить правильность результатов, полученных с помощью опросов, может оказаться полезным использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить необходимость сброса кэша и обновления перед вызовом методов получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Получение шрифт и цвет шрифта для текста выделение цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Доступ к хранимой шрифта и цветов](../extensibility/accessing-stored-font-and-color-settings.md)
- [Как: доступ к встроенных шрифтов и цветов](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Обзор цвет и шрифт](../extensibility/font-and-color-overview.md)
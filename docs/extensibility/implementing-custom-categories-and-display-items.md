---
title: Реализация пользовательских категорий и отображаемые элементы | Документация Майкрософт
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
ms.openlocfilehash: 850e4396c11cbd83f578304eed78a25042185a25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894642"
---
# <a name="implement-custom-categories-and-display-items"></a>Реализовать пользовательские категории и отображать элементы
VSPackage может предоставить контроль над шрифты и цвета текста для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) через пользовательские категории и отображаемые элементы.

 Пользовательские категории и отображаемые элементы находятся на **шрифты и цвета** страницу свойств. Чтобы открыть **шрифты и цвета** свойство страницы на **средства** меню, щелкните **параметры**. Разверните **среды** и нажмите кнопку **шрифты и цвета**.

 Если вы используете этот механизм, пакеты VSPackage должны реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейса и его связанных интерфейсах.

 В принципе, этот механизм можно использовать для изменения всех имеющихся **отображаемые элементы** и **категории** , содержащих их. Тем не менее, его не следует изменить **EditorCategory текст** или его **отображаемые элементы**. Дополнительные сведения см. в разделе [Общие сведения о шрифте и цвете](../extensibility/font-and-color-overview.md).

 Чтобы реализовать пользовательскую **категории** или **отображаемые элементы**, пакет VSPackage должен:

- Создание или определение категорий в реестре.

   Реализация IDE **шрифты и цвета** страницу свойств использует эти сведения для правильно запроса служба, поддерживающая данной категории.

- Создайте или укажите группы (необязательно) в реестре.

   Его можно использовать для определения группы, который представляет объединение двух или более категорий. Если определен группу, интегрированной среды разработки автоматически выполняет слияние подкатегории и распространяет отображаемых элементов в пределах группы.

- Реализация поддержки интегрированной среды разработки.

- Обрабатывать изменения шрифта и цвета.

  Сведения см. в разделе [доступа хранятся параметры шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Для создания и определения категорий

- Создать специальный тип категории записи реестра в разделе *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >*\FontAndColors\\ `<Category>`]*

   *\<Категория >* нелокализованное имя категории.

- Добавить в реестр с двумя значениями:

  |name|Тип|Данные|Описание|
  |----------|----------|----------|-----------------|
  |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для идентификации категории.|
  |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID VSPackage службы, которая поддерживает категории.|

  Служба, указанная в реестр необходимо предоставить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> для соответствующей категории.

## <a name="to-create-or-identify-groups"></a>Чтобы создать или определить группы

- Создать специальный тип категории записи реестра в разделе *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >*\FontAndColors\\*  \<группы >*]*

   *\<группы >* нелокализованное имя группы.

- Добавить в реестр с двумя значениями:

  |name|Тип|Данные|Описание|
  |----------|----------|----------|-----------------|
  |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для идентификации группы.|
  |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы, которая поддерживает категории.|

  Служба, указанная в реестр необходимо предоставить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> для соответствующей группы.

## <a name="to-implement-ide-support"></a>Для реализации поддержки интегрированной среды разработки

- Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, который возвращает либо <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейс или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс в интегрированную среду разработки для каждого **категории** или группе указан GUID.

- Для каждого **категории** он поддерживает, VSPackage реализует отдельный экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейс.

- Методы реализуется через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> необходимо указать с помощью интегрированной среды разработки:

  -   Списки **отображаемые элементы** в **категории.**

  -   Локализуемые имена для **отображаемые элементы**.

  -   Отображаемые сведения для каждого члена **категории**.

  > [!NOTE]
  >  Каждый **категории** должен содержать по крайней мере один **отображаемым элементом**.

- Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейса позволяет определить объединение несколько категорий.

   Его реализация предоставляет интегрированную среду разработки с помощью:

  -   Список **категории** , относятся к данной группе.

  -   Доступ к экземплярам <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> поддержки каждого **категории** в пределах группы.

  -   Имена локализуемых групп.

- Обновление интегрированной среды разработки:

   Интегрированная среда разработки кэширует сведения о **шрифта и цвета** параметры. Таким образом, после внесения любого изменения интегрированной среды разработки **шрифта и цвета** конфигурации, рекомендуется убедиться, что кэш не требует обновления.

  Обновление кэша осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс и может быть выполнено глобально или только на выбранных элементов.

## <a name="to-handle-font-and-color-changes"></a>Для обработки изменения шрифта и цвета
 Для правильной поддержки цветовое выделение текста, который отображает VSPackage, выделение цветом служба, поддерживающая VSPackage должен отвечать на инициированного пользователем изменения, внесенные через **шрифты и цвета** страница «свойства». VSPackage достигается путем:

-   Обработка события, вызываемые IDE путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> интерфейс.

     Интегрированная среда разработки вызывает соответствующий метод следующие пользовательские изменения из **шрифты и цвета** страницы. Например, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> метод, если выбран новый шрифт.

     - или -

-   Опрос для изменения интегрированной среды разработки.

     Это можно сделать через реализовать систему <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс. Несмотря на то что в основном для поддержки сохраняемости, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> метод может быть использован для получения данные шрифта и цвета для **отображаемые элементы**. Дополнительные сведения см. в разделе [доступа хранятся параметры шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Чтобы обеспечить правильность результатов, полученных опроса, часто бывает полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить необходимость сброса кэша и обновления перед вызовом методов извлечения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Получить данные шрифта и цвета для цветовое выделение текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Доступ хранимой параметры шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md)
- [Практическое: доступ к встроенной шрифтов и цветовой схемы](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Общие сведения о шрифте и цвете](../extensibility/font-and-color-overview.md)
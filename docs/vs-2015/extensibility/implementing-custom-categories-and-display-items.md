---
title: Реализация пользовательских категорий и отображение элементов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842609"
---
# <a name="implementing-custom-categories-and-display-items"></a>Реализация пользовательских категорий и отображаемых элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет VSPackage может обеспечить управление шрифтами и цветами своего текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среде разработки (IDE) с помощью пользовательских категорий и отображаемых элементов.  
  
 Пользовательские категории и отображаемые элементы находятся на странице свойств **шрифты и цвета** . Чтобы открыть страницу свойств **шрифты и цвета** , в меню **Сервис** выберите пункт **Параметры**. Разверните узел **Среда** и выберите пункт **шрифты и цвета**.  
  
 При использовании этого механизма пакеты VSPackage должны реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс и связанные с ним интерфейсы.  
  
 В принципе этот механизм можно использовать для изменения всех существующих **отображаемых элементов** и **категорий** , содержащих их. Однако его не следует использовать для изменения **текста едиторкатегори** или его **отображаемых элементов**. Дополнительные сведения см. в разделе [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md).  
  
 Для реализации пользовательских **категорий** или **отображаемых элементов**пакет VSPackage должен:  
  
- Создание или указание категорий в реестре.  
  
   Реализация страницы свойств **шрифтов и цветов** в интегрированной среде разработки использует эти сведения для правильного запроса службы, поддерживающей данную категорию.  
  
- Создание или указание групп (необязательно) в реестре.  
  
   Может быть полезно определить группу, которая представляет объединение двух или более категорий. Если группа определена, интегрированная среда разработки автоматически выполняет слияние подкатегорий и распространяет отображаемые элементы в группе.  
  
- Реализуйте поддержку интегрированной среды разработки.  
  
- Обрабатывайте изменения шрифта и цвета.  
  
  Дополнительные сведения см. в разделе [доступ к сохраненным параметрам шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Создание или указание категорий  
  
- Создайте запись реестра особого типа в разделе [Хклм\софтваре\микрософт \Висуал Studio \\ *\<Visual Studio version>* \фонтандколорс \\ `<Category>` ]  
  
   *\<Category>* нелокализованное имя категории.  
  
- Заполните реестр двумя значениями:  
  
  |Имя|Тип|Данные|Описание|  
  |----------|----------|----------|-----------------|  
  |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для задания категории.|  
  |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы VSPackage, которая поддерживает категорию.|  
  
  Служба, указанная в реестре, должна обеспечивать реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> для соответствующей категории.  
  
## <a name="to-create-or-identify-groups"></a>Создание или указание групп  
  
- Создайте запись реестра особого типа в разделе [Хклм\софтваре\микрософт \Висуал Studio \\ *\<Visual Studio version>* \фонтандколорс \\ *\<group>* ]  
  
   *\<group>* — Это нелокализованное имя группы.  
  
- Заполните реестр двумя значениями:  
  
  |Имя|Тип|Данные|Описание|  
  |----------|----------|----------|-----------------|  
  |Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для задания группы.|  
  |Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID службы, которая поддерживает категорию.|  
  
  Служба, указанная в реестре, должна обеспечивать реализацию `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` для соответствующей группы.  
  
## <a name="to-implement-ide-support"></a>Реализация поддержки интегрированной среды разработки  
  
- Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> метод, который возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейс или интерфейс `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` в интегрированную среду разработки для каждой указанной **категории** или GUID группы.  
  
- Для каждой поддерживаемой **категории** поддерживается пакет VSPackage, реализующий отдельный экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейса.  
  
- Методы, реализованные с помощью, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> должны предоставлять интегрированную среду разработки следующим образом:  
  
  - Списки **отображаемых элементов** в **категории.**  
  
  - Локализуемые имена для **отображаемых элементов**.  
  
  - Отображает сведения для каждого элемента **категории**.  
  
  > [!NOTE]
  > Каждая **Категория** должна содержать по крайней мере один **отображаемый элемент**.  
  
- Интегрированная среда разработки использует `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` интерфейс для определения объединения нескольких категорий.  
  
   Его реализация предоставляет интегрированную среду разработки:  
  
  - Список **категорий** , составляющих данную группу.  
  
  - Доступ к экземплярам, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> поддерживающим каждую **категорию** в группе.  
  
  - Локализуемые имена групп.  
  
- Обновление интегрированной среды разработки:  
  
   В интегрированной среде разработки кэшируются сведения о параметрах **шрифтов и цветов** . Таким образом, после любого изменения конфигурации **шрифта и цвета** IDE рекомендуется убедиться в том, что кэш обновлен.  
  
  Обновление кэша осуществляется через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс и может выполняться глобально или только для выбранных элементов.  
  
## <a name="to-handle-font-and-color-changes"></a>Для изменения шрифта и цвета  
 Для правильной поддержки цветовой раскраски текста, отображаемого VSPackage, служба цветов, поддерживающая VSPackage, должна реагировать на изменения, инициированные пользователем, на странице свойств **шрифты и цвета** . Пакет VSPackage выполняет следующие действия:  
  
- Обработка создаваемых интерфейсом IDE событий путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> интерфейса.  
  
     Интегрированная среда разработки вызывает соответствующий метод после изменения пользователем страницы **шрифты и цвета** . Например, он вызывает метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> Если выбран новый шрифт.  
  
     -или-  
  
- Опрос интегрированной среды разработки для внесения изменений.  
  
     Это можно сделать с помощью реализованного в системе <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса. Хотя в основном для поддержки сохраняемости, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> метод можно использовать для получения сведений о шрифтах и цветах для **отображаемых элементов**. Дополнительные сведения см. в разделе [доступ к сохраненным параметрам шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Чтобы гарантировать правильность результатов опроса, может быть полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуются ли операции очистки и обновления кэша перед вызовом методов получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Получение сведений о шрифтах и цветах для цветовой раскраски текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Доступ к сохраненным параметрам шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Пошаговое руководство. доступ к встроенным шрифтам и цветовой схеме](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md)

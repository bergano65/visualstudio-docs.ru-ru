---
title: "Как: Создание настраиваемых текстовых маркеров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ab395fdb8c06e643c76ee0918b8a626abb756cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-custom-text-markers"></a>Как: Создание настраиваемых текстовых маркеров
Если требуется создать пользовательские текстовая метка выделить или организации кода, необходимо выполнить следующие действия:  
  
-   Регистрация текстового маркера доступа к нему другие средства  
  
-   Реализация по умолчанию и конфигурации текстовой метки  
  
-   Создать службу, которая может использоваться другими процессами, чтобы сделать использование текстовой метки  
  
 Дополнительные сведения о том, как применить текстовая метка в область кода, в разделе [как: использование текстовых маркеров](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Для регистрации пользовательских маркеров  
  
1.  Создайте запись реестра следующим образом:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >*маркеры \Text Editor\External\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*— `GUID` используется для идентификации добавляемого маркера  
  
     *\<Версия >* версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 8.0  
  
     *\<PackageGUID >* — это GUID пакета VSPackage, реализующий объект автоматизации.  
  
    > [!NOTE]
    >  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* может быть переопределен с альтернативным корнем при инициализации оболочки Visual Studio, дополнительная информация [Параметры командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Создание четырех значений в группе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >*\Text Editor\External маркеры\\*\<MarkerGUID >*  
  
    -   (Значение по умолчанию)  
  
    -   Служба  
  
    -   DisplayName  
  
    -   Пакет  
  
    -   `Default`является необязательным элементом типа REG_SZ. Если задано значение параметра является строкой, содержащей некоторые полезные идентификационные данные, например «Custom текстовая метка».  
  
    -   `Service`запись типа REG_SZ содержащего строка GUID службы, которая предоставляет пользовательский текст маркера, proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName`запись типа REG_SZ, содержащий идентификатор ресурса с именем пользовательского текстовой метки. Формат — #YYYY.  
  
    -   `Package`запись типа REG_SZ, содержащего `GUID` VSPackage, предоставляющего службу, создаваемых в рамках службы. Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Для создания маркера пользовательского текста  
  
1.  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Реализации этого интерфейса определяет поведение и внешний вид ваш тип пользовательского маркера.  
  
     Этот интерфейс называется  
  
    1.  Пользователь запускает интегрированную среду разработки в первый раз.  
  
    2.  Пользователь выбирает **сброс значения по умолчанию** под заголовком **шрифты и цвета** на странице свойств в **среды** папка на левой панели  **Параметры** диалоговое окно полученный от **средства** меню интегрированной среды разработки.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> метод, указывая, что `IVsPackageDefinedTextMarkerType` реализации должны быть возвращаются в зависимости от типа маркера GUID, указанный в вызове метода.  
  
     Окружение вызывает этот метод первый во время вашего типа пользовательских маркеров создается и указывает идентификатор GUID, определяющий тип пользовательского маркера.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Чтобы proffer ваш тип маркера в качестве службы  
  
1.  Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> возвращается.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> метод, указывая GUID идентификации типа службы пользовательских маркеров и предоставляя указатель на вашу реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейса. Ваш <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> реализации должен возвращать указатель на вашу реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> интерфейса.  
  
     Уникальный файл cookie, указывающий, что возвращается к службе. Позже можно использовать этот файл cookie отменять пользовательских маркеров типа службы путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейс указано это значение файла cookie.  
  
## <a name="see-also"></a>См. также  
 [С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Как: Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)   
 [Как: реализовать маркеры ошибки](../extensibility/how-to-implement-error-markers.md)   
 [Как: использовать маркеры текста](../extensibility/how-to-use-text-markers.md)
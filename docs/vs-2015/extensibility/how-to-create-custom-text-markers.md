---
title: Создание настраиваемых маркеров текста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842381"
---
# <a name="how-to-create-custom-text-markers"></a>Практическое руководство. Создание пользовательских текстовых маркеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы хотите создать настраиваемый текстовый маркер для акцентирования или организации кода, необходимо выполнить следующие действия.  
  
- Зарегистрируйте новый текстовый маркер, чтобы другие средства могли получить к нему доступ.  
  
- Предоставление реализации и конфигурации по умолчанию для текстового маркера  
  
- Создание службы, которая может использоваться другими процессами для использования текстового маркера  
  
  Дополнительные сведения о применении текстового маркера к области кода см. [в разделе как использовать текстовые маркеры](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Регистрация пользовательского маркера  
  
1. Создайте запись реестра следующим образом:  
  
    HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* \Текст едитор\екстернал маркеры\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>`GUID`используется для обнаружения добавляемого маркера  
  
    *\<Version>* версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , например 8,0  
  
    *\<PackageGUID>* Идентификатор GUID для пакета VSPackage, реализующего объект автоматизации.  
  
   > [!NOTE]
   > Корневой путь HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* можно переопределить с помощью альтернативного корня при инициализации оболочки Visual Studio. Дополнительные сведения см. в разделе [Параметры командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Создайте четыре значения в разделе HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* \Текст едитор\екстернал маркеры.\\*\<MarkerGUID>*  
  
   - (по умолчанию)  
  
   - Служба  
  
   - DisplayName  
  
   - Пакет  
  
   - `Default` является необязательной записью типа REG_SZ. Если задано значение, значением записи является строка, содержащая некоторые полезные идентифицирующие сведения, например "пользовательский текст маркер".  
  
   - `Service` — это запись типа REG_SZ, содержащая строку GUID службы, предоставляющей пользовательский маркер текста по профферинг <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` — это запись типа REG_SZ, содержащая идентификатор ресурса имени пользовательского текстового маркера. Формат #YYYY.  
  
   - `Package` запись типа REG_SZ `GUID` , содержащая пакет VSPackage, предоставляющий службу, указанную в разделе Служба. Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Создание пользовательского маркера текста  
  
1. Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Реализация этого интерфейса определяет поведение и внешний вид пользовательского типа маркера.  
  
     Этот интерфейс вызывается, когда  
  
    1. Пользователь запускает интегрированную среду разработки в первый раз.  
  
    2. Пользователь нажимает кнопку **Сброс значений по умолчанию** на странице свойств **шрифты и цвета** в папке **Среда** , расположенной в левой области диалогового окна **Параметры** , полученной из меню **Сервис** интегрированной среды разработки.  
  
2. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> метод, указав, какая `IVsPackageDefinedTextMarkerType` реализация должна возвращаться на основе идентификатора GUID типа маркера, указанного в вызове метода.  
  
     Среда вызывает этот метод при первом создании пользовательского типа маркера и задает идентификатор GUID, определяющий тип пользовательского маркера.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Предложить типа маркера как услуги  
  
1. Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> метод для <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> метод, указав идентификатор GUID, определяющий службу пользовательского типа маркера, и указав указатель на свою реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейса. Ваша <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> реализация должна возвращать указатель на вашу реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> интерфейса.  
  
     Уникальный файл cookie, указывающий, что служба возвращена. Позже этот файл cookie можно использовать для отзыва службы пользовательского типа маркера путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метода <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейса, указывающего это значение файла cookie.  
  
## <a name="see-also"></a>См. также:  
 [Использование текстовых маркеров с устаревшим API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Руководство. Добавление стандартных текстовых маркеров](../extensibility/how-to-add-standard-text-markers.md)   
 [Как реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)   
 [Практическое руководство. Использование текстовых маркеров](../extensibility/how-to-use-text-markers.md)

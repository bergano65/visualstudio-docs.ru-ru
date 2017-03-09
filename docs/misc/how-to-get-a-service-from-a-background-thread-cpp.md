---
title: "Практическое руководство: доступ к службе из фонового потока (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "многопоточность, службы"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Практическое руководство: доступ к службе из фонового потока (C++)
Невозможно получить посредством службы `IServiceProvider.QueryService` из фонового потока.  При использовании `QueryService` получить службу в основном потоке, а затем попробовать использовать службу в фоновом потоке, он также не удастся.  
  
 Чтобы получить службу из фонового потока, используйте `CoMarshalInterThreadInterfaceInStream` в  `IVsPackage.SetSite` метод, чтобы маршалировать поставщик услуг в поток в основном потоке.  После этого можно unmarshal поставщик услуг в фоновом потоке и использовать ее для получения службы.  Можно unmarshal только один раз, поэтому поместить интерфейс в кэше, можно получить обратно.  
  
> [!NOTE]
>  Управляемый код автоматически маршалирует интерфейсов между потоками, поэтому получение службу из фонового потока не требуют специального кода.  
  
## Пример  
 В следующем коде маршалирует поставщик услуг в основном потоке, и обеспечивает a `QueryServiceFromBackgroundThread` метод unmarshal поставщик служб для получения службу из фонового потока.  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## См. также  
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)
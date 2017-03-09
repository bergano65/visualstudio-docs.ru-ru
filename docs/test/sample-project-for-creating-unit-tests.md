---
title: "Пример проекта для создания модульных тестов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пример модульного теста [Visual Studio]"
  - "модульные тесты, примеры"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Пример проекта для создания модульных тестов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот пример кода предназначен для использования в указанных ниже пошаговых руководствах.  
  
-   [Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Пошаговое руководство по созданию и настройке модульных тестов, их выполнению и изучению результатов.  
  
-   [Пошаговое руководство. Запуск тестов и просмотр покрытия кода](http://msdn.microsoft.com/ru-ru/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  В этом пошаговом руководстве описан порядок просмотра данных о покрытии кода, отражающих тестируемую часть кода проекта.  
  
-   [Пошаговое руководство. Использование служебной программы для тестирования с интерфейсом командной строки](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  В этом пошаговом руководстве с помощью программы командной строки MSTest.exe выполняются тесты и просматриваются результаты.  
  
## Пример кода  
 Единственная умышленно допущенная в этом примере ошибка заключается в том, что у метода Debit в m\_balance \+\= amount вместо знака плюс перед знаком равно должен стоять минус.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 \/\* Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными.  Любые совпадения с реальными именами и названиями случайны.  \*\/  
  
## Работа с кодом  
 Для работы с этим кодом необходимо сначала создать для него проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Следуйте инструкциям в подразделе «Подготовка к выполнению пошагового руководства» раздела [Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## См. также  
 [Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Пошаговое руководство. Запуск тестов и просмотр покрытия кода](http://msdn.microsoft.com/ru-ru/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Пошаговое руководство. Использование служебной программы для тестирования с интерфейсом командной строки](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)
---
title: Executar uma consulta XPath em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 6082a171d24c55ea52c153bbd920bb7486be78a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784368"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Executar uma consulta XPath em um DataSet
A relação entre um <xref:System.Data.DataSet> sincronizado <xref:System.Xml.XmlDataDocument> e permite que você faça uso de serviços XML, como a consulta XPath, que acessa o **XmlDataDocument** e pode executar determinada funcionalidade de forma mais conveniente do que Acessando o **conjunto** de os diretamente. Por exemplo, em vez de usar o método **Select** de <xref:System.Data.DataTable> a para navegar em relações com outras tabelas em um conjunto de um **DataSet**, você pode executar uma consulta XPath em um **XmlDataDocument** que é sincronizado com o **DataSet**, para obter um lista de elementos XML na forma de um <xref:System.Xml.XmlNodeList>. Os nós na **XmlNodeList**, Cast como <xref:System.Xml.XmlElement> Nodes, podem ser passados para o método **GetRowFromElement** de **XmlDataDocument**, para retornar referências correspondentes <xref:System.Data.DataRow> às linhas da tabela no  **Conjunto**de um.  
  
 Por exemplo, o exemplo de código a seguir executa uma consulta XPath "neto". O **DataSet** é preenchido com três tabelas: **Clientes**, **pedidos**e **OrderDetails**. No exemplo, uma relação pai-filho é criada primeiro entre as tabelas **Customers** e **Orders** e entre as tabelas **Orders** e **OrderDetails** . Em seguida, uma consulta XPath é executada para retornar um XmlNodeList **de nós** de **clientes** em que um nó neto **OrderDetails** tem um nó **ProductID** com o valor de 43. Em essência, o exemplo está usando a consulta XPath para determinar quais clientes solicitaram o produto com o **ProductID** de 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Sincronização de DataSet e XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)

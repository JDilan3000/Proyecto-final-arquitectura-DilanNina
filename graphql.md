# Documentación del Esquema de Datos: GraphQL Implementation

Este documento describe la capa de consulta de datos diseñada para optimizar la eficiencia del ancho de banda y mejorar la experiencia de desarrollo mediante un sistema de tipos fuertes.

## 1. Justificación de Implementación
Se utiliza GraphQL para mitigar los problemas de *Over-fetching* y *Under-fetching* identificados en interfaces REST tradicionales, permitiendo a los clientes definir la forma exacta de la respuesta.

## 2. Definición de Tipos de Objeto (Schema Definition Language)
```graphql
"""
Representa una unidad de trabajo dentro del sistema.
"""
type Task {
  id: ID!
  title: String!
  description: String
  status: TaskStatus!
  createdAt: String
  updatedAt: String
  assignedDeveloper: User
}

enum TaskStatus {
  BACKLOG
  IN_PROGRESS
  COMPLETED
}

type User {
  id: ID!
  name: String
  email: String
  role: String
}

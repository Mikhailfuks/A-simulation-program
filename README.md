using System;
using System.Collections.Generic;
using System.Linq;

namespace Simulation
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Добро пожаловать в симулятор!");

            // Создаем мир
            World world = new World();

            // Добавляем агентов
            world.AddAgent(new Agent("Агент 1", 10));
            world.AddAgent(new Agent("Агент 2", 5));

            // Запускаем симуляцию
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine($"\nШаг {i + 1}:");
                world.SimulateStep();
                world.PrintState();
            }

            Console.ReadKey();
        }
    }

    // Класс для представления мира
    class World
    {
        private List<Agent> agents;

        public World()
        {
            agents = new List<Agent>();
        }

        // Добавляем нового агента
        public void AddAgent(Agent agent)
        {
            agents.Add(agent);
        }

        // Выполняем шаг симуляции
        public void SimulateStep()
        {
            // Каждый агент выполняет действие
            foreach (Agent agent in agents)
            {
                agent.Act();
            }
        }

        // Выводим состояние мира
        public void PrintState()
        {
            foreach (Agent agent in agents)
            {
                Console.WriteLine($"{agent.Name}: {agent.Resource}");
            }
        }
    }

    // Класс для представления агента
    class Agent
    {
        public string Name { get; set; }
        public int Resource { get; set; }

        public Agent(string name, int resource)
        {
            Name = name;
            Resource = resource;
        }

        // Выполняет действие агента
        public void Act()
        {
            // Простое действие: увеличивает ресурс на 1
            Resource++;
        }
    }
}

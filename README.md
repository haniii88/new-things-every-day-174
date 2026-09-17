function dailyLog174() {
  const resources = [
    { name: "CPU", used: 72, capacity: 100 },
    { name: "Memory", used: 58, capacity: 80 },
    { name: "Storage", used: 420, capacity: 500 },
    { name: "Network", used: 65, capacity: 100 }
  ];

  const report = resources.map(resource => ({
    name: resource.name,
    usage: `${((resource.used / resource.capacity) * 100).toFixed(1)}%`,
    remaining: resource.capacity - resource.use
  }));

  const mostUtilized = resources.reduce((max, resource) =>
    resource.used / resource.capacity > max.used / max.capacity
      ? resource
      : max
  );

  console.log("Daily Resource Report:", {
    date: new Date().toISOString().split("T")[0],
    resources: report,
    mostUtilized: mostUtilized.name
  });
}

dailyLog174();

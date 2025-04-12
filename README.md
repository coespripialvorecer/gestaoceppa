function AdminDashboard() {
  const [pendingRegistrations, setPendingRegistrations] = useState([
    { id: 1, email: "novo@aluno.com", role: "aluno" },
    { id: 2, email: "professor@escola.com", role: "professor" },
  ]);

  const handleApprove = (id) => {
    setPendingRegistrations((prevState) =>
      prevState.filter((registration) => registration.id !== id)
    );
    alert("Inscrição aprovada!");
  };

  const handleReject = (id) => {
    setPendingRegistrations((prevState) =>
      prevState.filter((registration) => registration.id !== id)
    );
    alert("Inscrição rejeitada!");
  };

  return (
    <section className="bg-white rounded-2xl shadow p-6">
      <h2 className="text-2xl font-semibold mb-4 text-blue-600">
        <FaUserTie className="inline-block mr-2 text-blue-600" /> Área de Administração
      </h2>
      <h3 className="text-xl mb-4">Inscrições Pendentes</h3>
      <ul>
        {pendingRegistrations.map((registration) => (
          <li key={registration.id} className="mb-4">
            <p>
              <strong>Email:</strong> {registration.email} <br />
              <strong>Função:</strong> {registration.role}
            </p>
            <div className="mt-2">
              <button
                onClick={() => handleApprove(registration.id)}
                className="bg-green-500 text-white px-4 py-2 rounded-md mr-2"
              >
                Aprovar
              </button>
              <button
                onClick={() => handleReject(registration.id)}
                className="bg-red-500 text-white px-4 py-2 rounded-md"
              >
                Rejeitar
              </button>
            </div>
          </li>
        ))}
      </ul>
    </section>
  );
}

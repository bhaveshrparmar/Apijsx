import { useState } from "react";

export default function API() {
  const [users, setUsers] = useState([]);

  async function ShowAPI() {
    const res = await fetch("https://jsonplaceholder.typicode.com/users");
    const data = await res.json();
    setUsers(data);
  }

  console.log("data....");
  console.log(users);

  return (
    <div className="container py-4">
      <button className="btn btn-primary mb-3" onClick={ShowAPI}>
        ShowAPI
      </button>

      <table className="table table-bordered table-striped">
        <thead className="table-dark">
          <tr>
            <th>#</th>
            <th>Name</th>
            <th>Email</th>
            <th>Number</th>
          </tr>
        </thead>
        <tbody>
          {users.map((user, index) => (
            <tr key={user.id}>
              <td>{index + 1}</td>
              <td>{user.name}</td>
              <td>{user.email}</td>
              <td>{user.phone}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
}

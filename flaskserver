from flask import Flask, jsonify, request, make_response
from datetime import datetime
app = Flask(__name__)


@app.route('/endpoint1', methods=['GET'])
def endpoint1():
    now = datetime.now()
    notes = [{"year": now.year, "month": now.month, "day": now.day}] * 10000
    response = make_response(jsonify(notes))
    response.headers['Cache-Control'] = 'public, max-age=600'
    return response


@app.route('/endpoint2', methods=['POST'])
def endpoint2():
    name = request.form.get('name')
    if not name:
        return jsonify({"error": "Missing 'name' parameter in the form request"}), 400

    notes = [{"name": name}] * 10000
    response = make_response(jsonify(notes))
    response.headers['Cache-Control'] = 'public, max-age=600'
    return response


if __name__ == '__main__':
    app.run(debug=True)
